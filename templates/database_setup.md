# database_connection.rb
require 'pg'

class DatabaseConnection
  def self.connect(database)
    @connection = PG.connect({ host: '127.0.0.1', dbname: database })
  end

  def self.exec_params(query, params)
    if @connection.nil?
      raise 'DatabaseConnection.exec_params: Cannot run a SQL query as the connection to'\
      'the database was never opened. Did you make sure to call first the method '\
      '`DatabaseConnection.connect` in your app.rb file (or in your tests spec_helper.rb)?'
    end
    @connection.exec_params(query, params)
  end
end

# spec_helper.rb
require 'database_connection'

DatabaseConnection.connect('database_test')

# app.rb

require_relative 'lib/database_connection'
require_relative "lib/table_repository"

DatabaseConnection.connect('database')

# seeds_table.sql
TRUNCATE TABLE artists RESTART IDENTITY; 
TRUNCATE TABLE albums RESTART IDENTITY;

INSERT INTO artists (name, genre) VALUES ('Linkin Park', 'Alternative Rock');

INSERT INTO albums (title, release_year, artist_id) VALUES ('Hybrid theory', '2000', 1);
INSERT INTO albums (title, release_year, artist_id) VALUES ('Meteora', '2003', 1);

# seed example
DROP TABLE IF EXISTS "public"."books";
-- This script only contains the table creation statements and does not fully represent the table in the database. It's still missing: indices, triggers. Do not use it as a backup.

-- Sequence and defined type
CREATE SEQUENCE IF NOT EXISTS books_id_seq;

-- Table Definition
CREATE TABLE "public"."books" (
    "id" SERIAL,
    "title" text,
    "author_name" text,
    PRIMARY KEY ("id")
);

INSERT INTO "public"."books" ("id", "title", "author_name") VALUES
(1, 'Nineteen Eighty-Four', 'George Orwell'),
(2, 'Mrs Dalloway', 'Virginia Woolf'),
(3, 'Emma', 'Jane Austen'),
(4, 'Dracula', 'Bram Stoker'),
(5, 'The Age of Innocence', 'Edith Wharton');