# Project Resolution Tracker App 🚀

Welcome to the **Project Resolution Tracker App**! This application helps you document and manage solutions to technical challenges encountered during your project work. It's built with a Supabase backend and a React frontend, designed to be simple, functional, and visually appealing.

## ✨ Features

*   **📝 Store Resolution Details**: Keep a structured log of issues and their resolutions.
*   **🔑 Secure Key/Secret Storage**: A dedicated table for managing API keys and other sensitive credentials (with a reminder to use proper encryption in production).
*   **🗂️ Categorization & Sub-categorization**:
    *   **Categories**: Salesforce, MuleSoft, nvim, Other.
    *   **Subcategories (Dynamic based on Category)**:
        *   Salesforce: Apex, LWC, Flow, Permissions, Other
        *   MuleSoft: DataWeave, POM, Flow, Other
        *   nvim: Plugins, Coding, Other
*   **🔍 Powerful Search & Filtering**:
    *   Query resolutions by category, subcategory, and creation date.
    *   Free-text search within resolution details.
*   **➕ CRUD Operations**: Easily Add, View, Edit, and Delete resolutions.
*   **📊 Basic Reporting & Dashboard**: Visualize the number of entries per category.
*   **💡 Conditional UI**: Smart forms that adapt (e.g., subcategory options appear after selecting a category).
*   **✅ Input Validation**: Ensures data integrity, like making all fields mandatory before submission.

## 🛠️ Tech Stack

*   **Backend**: [Supabase](https://supabase.io/) - PostgreSQL database, Authentication, and auto-generated APIs.
*   **Frontend**: [React](https://reactjs.org/) - A JavaScript library for building user interfaces.
*   **Styling**: (To be decided - e.g., Tailwind CSS, Material UI, etc.)
*   **Deployment**: (To be decided - e.g., Vercel, Netlify)

## 🚀 Getting Started

*(Instructions on how to set up and run the project locally will be added here once the initial development is done.)*

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/ovuceljic/project-resolution-tracker-app.git
    cd project-resolution-tracker-app
    ```
2.  **Install dependencies:**
    ```bash
    # Frontend (assuming npm)
    cd frontend # or appropriate directory
    npm install

    # Backend setup will involve Supabase project configuration.
    ```
3.  **Configure Supabase:**
    *   Create a `.env` file in your frontend project.
    *   Add your Supabase Project URL and Anon Key:
        ```env
        REACT_APP_SUPABASE_URL=YOUR_SUPABASE_URL
        REACT_APP_SUPABASE_ANON_KEY=YOUR_SUPABASE_ANON_KEY
        ```
4.  **Run the application:**
    ```bash
    # Frontend (assuming npm)
    npm start
    ```

## DB Schema Overview

### `secure_configurations`
Stores API keys, secrets, and other sensitive configuration data.
| Column         | Type      | Constraints          | Notes                                                                 |
| -------------- | --------- | -------------------- | --------------------------------------------------------------------- |
| id             | BIGINT    | PRIMARY KEY, SERIAL  |                                                                       |
| service_name   | TEXT      | NOT NULL             | e.g., "AWS", "Salesforce API"                                         |
| key_name       | TEXT      | NOT NULL             | e.g., "Access Key ID", "Client Secret"                               |
| key_value      | TEXT      | NOT NULL             | **Warning**: Encrypt this in production (e.g., using Supabase Vault). |
| created_at     | TIMESTAMPTZ| DEFAULT now()        |                                                                       |

### `resolutions`
Stores details about project resolutions, categorized for easy searching and analysis.
| Column             | Type      | Constraints                                                  | Notes                                           |
| ------------------ | --------- | ------------------------------------------------------------ | ----------------------------------------------- |
| id                 | BIGINT    | PRIMARY KEY, SERIAL                                          |                                                 |
| category           | TEXT      | NOT NULL, CHECK (category IN ('salesforce', 'mulesoft', 'nvim', 'other')) |                                                 |
| subcategory        | TEXT      |                                                              | Frontend managed based on category              |
| resolution_details | TEXT      | NOT NULL                                                     | Long text field for detailed resolution steps   |
| created_at         | TIMESTAMPTZ| DEFAULT now()                                                | For sorting and querying by date                |

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

*(Guidelines for contributing will be added here.)*

## 📄 License

This project is licensed under the MIT License - see the `LICENSE` file for details (if you add one).
