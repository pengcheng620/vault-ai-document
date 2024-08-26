## 2024-08-26
- **Q0**: What is implemented so far regarding search, and what are the hints on how to ask questions regarding
  combining properties to call the search APIs?
- **A0**: Currently, we can only search for a single condition. We plan to implement multiple conditions. For more
  details on searchable properties, please see the following question.

- **Q1**: What are the searchable properties? For example, I tried Material, Description, and a few other properties
  that didn't work, while File Name, Revision, and State sometimes did.
- **A1**: The searchable properties are user-defined custom properties. There are many (currently 213 in our database),
  so we can't list all of them. We plan to add more properties (like Material, Description, etc.) to the searchable
  list.

    - Currently, we hard-code these searchable properties. Here is a table of some searchable properties:

      | Property                        | Description              |
            |---------------------------------|--------------------------|
      | Classification                  | Classification           |
      | Version                         | Version Number           |
      | Comment                         | Comment                  |
      | Date Version Created            | Date Version Created     |
      | Created By                      | Create User Name         |
      | Create Date                     | Create Date              |
      | Checked In                      | Check In Date            |
      | File Name                       | Client File Name         |
      | Date Modified                   | Mod Date                 |
      | File Size                       | File Size                |
      | Checked Out                     | Checkout Date            |
      | Checked Out By                  | Checkout User Name       |
      | Latest Version                  | Latest Version           |
      | Folder Path                     | Folder Path              |
      | Lifecycle Definition            | Life Cycle Definition    |
      | State                           | State                    |
      | Revision                        | Revision                 |
      | Last Updated By                 | Last Modified User Name  |
      | Title                           | Title                    |
      | Company                         | Company                  |
      | Date File Created               | Creation Date            |

    - **Note:** Even in a production environment, we can't list all searchable properties because:
        1. The list is dynamic and will grow with user needs.
        2. Many properties are user-defined and may be duplicated.
        3. Searching too many properties can impact performance and accuracy.

    - **Future Solutions:**
        - **Predefined:** Sync all properties when entering the AI-Bot and feed the results to the AI model to list
          important properties.
        - **Synchronized:** Sync user-defined properties during user input and search based on the input.


- **Q2**: What conditions are implemented?
- **A2**: Here is a table of the currently supported conditions:

  | Operator             | Description                                                     |
    |----------------------|-----------------------------------------------------------------|
  | Contains             | Checks if a value contains a specified substring                |
  | DoesNotContain       | Checks if a value does not contain a specified substring        |
  | IsExactly            | Checks if a value is exactly equal to a specified value         |
  | IsEmpty              | Checks if a value is empty                                      |
  | IsNotEmpty           | Checks if a value is not empty                                  |
  | GreaterThan          | Checks if a value is greater than a specified value             |
  | GreaterThanOrEqualTo | Checks if a value is greater than or equal to a specified value |
  | LessThan             | Checks if a value is less than a specified value                |
  | LessThanOrEqualTo    | Checks if a value is less than or equal to a specified value    |
  | NotEqualTo           | Checks if a value is not equal to a specified value             |

- **Q3**: Did we implement an "AND" operator or at the moment it is just one prop and one value?
- **A3**: No, the "AND" operator is not implemented yet. Currently, only one property and one value are supported. We
  are planning to implement the "AND" operator.


- **Q4**: Did we implement search in multiple prop? e.g. find files with "Turbine" and it will find all files where
  e.g.,
  Turbine is part of Title, Description or name of the file.
- **A4**: No, this is not implemented yet. Currently, we are planning to implement this.

- **Q5**: Accuracy: example show me file with name water heater.iam. Vault results are 1. Chatbot results are 6. All
  versions of
  the heater.iam are shown in the results. I Think we need to add an argument to show an entry only once the results.
- **A5**: Yes, this is under review, and we plan to implement it.