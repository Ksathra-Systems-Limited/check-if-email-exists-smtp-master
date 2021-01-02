# check-if-smtp-email-exists-master

Use it in your code as follows:

use check_if_email_exists::{check_email, CheckEmailInput};

async fn check() {
    // Imagin we want to test the deliverability of someone@gmail.com.
    let mut input = CheckEmailInput::new(vec!["someone@gmail.com".into()]);

    // Optionally, we can also tweak the configuration parameters used in the
    // verification.
    input
        .from_email("me@example.org".into()) // Used in the `MAIL FROM:` command
        .hello_name("example.org".into()); // Used in the `EHLO` command

    // Verify this input, using async/await syntax.
    let result = check_email(&input).await;

    // `result` is a `Vec<CheckEmailOutput>`, where the CheckEmailOutput
    // struct contains all information about our email.
    println!("{:?}", result);
}
```
## ✈️ JSON Output
The output will be a JSON with the below format, the fields should be self-explanatory. 
For `someone@gmail.com` (note that it is disabled by Gmail);
