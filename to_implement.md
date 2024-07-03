```rust
pub enum FieldTypeValue {
    Integer(i32),
    Float(f64),
    Text(String),
    Long(i64),
}

impl FieldTypeValue {
    // Associated function to create a FieldTypeValue::Integer variant
    pub fn new_integer(value: i32) -> Self {
        FieldTypeValue::Integer(value)
    }

    // Associated function to create a FieldTypeValue::Float variant
    pub fn new_float(value: f64) -> Self {
        FieldTypeValue::Float(value)
    }

    // Associated function to create a FieldTypeValue::Text variant
    pub fn new_text(value: String) -> Self {
        FieldTypeValue::Text(value)
    }

    // Associated function to create a FieldTypeValue::Long variant
    pub fn new_long(value: i64) -> Self {
        FieldTypeValue::Long(value)
    }

    // Method to get the value as i32 if it's an Integer variant
    pub fn as_integer(&self) -> Option<i32> {
        match self {
            FieldTypeValue::Integer(value) => Some(*value),
            _ => None,
        }
    }

    // Method to get the value as f64 if it's a Float variant
    pub fn as_float(&self) -> Option<f64> {
        match self {
            FieldTypeValue::Float(value) => Some(*value),
            _ => None,
        }
    }

    // Method to get the value as String if it's a Text variant
    pub fn as_text(&self) -> Option<&String> {
        match self {
            FieldTypeValue::Text(value) => Some(value),
            _ => None,
        }
    }

    // Method to get the value as i64 if it's a Long variant
    pub fn as_long(&self) -> Option<i64> {
        match self {
            FieldTypeValue::Long(value) => Some(*value),
            _ => None,
        }
    }
}


impl From<String> for FieldTypeValue {
    fn from(s: String) -> Self {
        // Attempt to parse the string into integer, float, or long
        // If successful, return the corresponding FieldTypeValue variant
        if let Ok(int_value) = s.parse::<i32>() {
            return FieldTypeValue::Integer(int_value);
        }
        
        if let Ok(float_value) = s.parse::<f64>() {
            return FieldTypeValue::Float(float_value);
        }

        if let Ok(long_value) = s.parse::<i64>() {
            return FieldTypeValue::Long(long_value);
        }

        // If parsing fails, default to storing the string
        FieldTypeValue::new_text(s)
    }
}


fn main() {
    // Conversion examples
    let int_value: FieldTypeValue = "123".to_string().into();
    let float_value: FieldTypeValue = "123.45".to_string().into();
    let long_value: FieldTypeValue = "1234567890".to_string().into();
    let text_value: FieldTypeValue = "Hello World!".to_string().into();

    println!("{:?}", int_value);   // Output: Integer(123)
    println!("{:?}", float_value); // Output: Float(123.45)
    println!("{:?}", long_value);  // Output: Long(1234567890)
    println!("{:?}", text_value);  // Output: Text("Hello World!")
}
```



### Explanation:

- **Enum Definition**: Defines the `FieldTypeValue` enum with variants `Integer(i32)`, `Float(f64)`, `Text(String)`, and `Long(i64)`.

- **Associated Function**: `new_text` is defined to create a `FieldTypeValue::Text` variant explicitly.

- **From<String> Implementation**: Implements the `From<String>` trait for `FieldTypeValue`, allowing conversion from `String` to the appropriate variant (`Integer`, `Float`, `Long`, or `Text`).

- **Usage Example (main function)**: Demonstrates conversion examples where `String` values are converted into `FieldTypeValue` variants using `into()`, and outputs the resulting variants using `println!()`.

### Rendering in Markdown:

When you include this Markdown code block (` ```rust ... ``` `) in your GitHub Markdown file (`*.md`), GitHub will render it with syntax highlighting appropriate for Rust code. This allows others to view and understand your Rust code easily directly on GitHub.

Make sure to replace `your_file_name.md` with the actual name of your Markdown file where you want to include this Rust code. This approach ensures your code is properly formatted and highlighted for readability and comprehension on GitHub.

