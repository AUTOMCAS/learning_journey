## 1. Describe the problem
*Break down the brief*


## 2. Design 

**Diagram:**
    The methods each class will contain.
    How the classes interact with each other.

**Interface:**

````
class ClassCollection
  Initialize
    # ...
  end

  def add_something(parameters)
  end

  def return_something
    # Returns?
  end

  def do_something
    # Returns?
  end
end

class ClassInstance
  Initialize(parameters) # Content type?
    # ...
  end

  def add_something(parameters)
  end

  def do_something
    # Returns based on whatever manipulation, calculation or condition.
  end
end
````

## 3 Create examples as Integration tests

Write out tests for each part of the brief.

**Brief part 1**
  **test 1**
    class = Class.new
    class.add(ClassInstance.new)(parameters)
    expect(class.do_something).to eq brief_requirement_output

  **test 2 - nothing readable**
    class = Class.new
    class.add(ClassInstance.new)(parameters)
    expect(class.do_something).to eq nil  
  
  **test 2 - error case**
    class = Class.new
    expect{ class.do_something }.to raise_error "Cannot divide by 0"


**INTEGRATION TEST TEMPLATE**

```
describe "class integration" do
  it "Adds ClassInstances to list / lists ClassInstances added" do

  describe "method behavior" do
    context "context when the test is run, eg entries added" do
      it "expected outcome 1" do
      end

      it "expected outcome 2" do
      end
    end

    context "nothing returnable" do
      it "returns nil" do
      end

      it "expected outcome 2" do
      end
    end
  end

  describe "method _2 behavior" do
    context "when something has happened, eg tracks added" do
      it "expected outcome 1" do
      end

      it "expected outcome 2" do
      end
    end

    context "when given something invalid" do
      it "fails" do
        {}raise_error "Error"
      end
    end
  end
end
```

# 4 Create examples as unit tests

Do this as you go along

```
**UNIT**
  describe "Class" do
    it "initially has/is empty ..." do
    end
  end

**UNIT which is integrated as an instance**
  describe "Class" do
    it "constructs" do
      # add entries
    end
  end
```

# 5 Implement the Behavior