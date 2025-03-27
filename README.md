its DevStarter CLI tool that generates project boilerplates for Python, Java, and Ruby.

import os
import shutil
import argparse

templates = {
    "python": "templates/python_template",
    "java": "templates/java_template",
    "ruby": "templates/ruby_template"
}

def create_project(project_name, language):
    if language not in templates:
        print(f"Error: Language '{language}' is not supported.")
        return
    
    template_path = templates[language]
    project_path = os.path.join(os.getcwd(), project_name)
    
    if os.path.exists(project_path):
        print(f"Error: Directory '{project_name}' already exists.")
        return
    
    shutil.copytree(template_path, project_path)
    print(f"Success: '{project_name}' created with {language} template.")

def main():
    parser = argparse.ArgumentParser(description="DevStarter - Create project boilerplates effortlessly.")
    parser.add_argument("name", help="Project name")
    parser.add_argument("language", choices=["python", "java", "ruby"], help="Programming language")
    
    args = parser.parse_args()
    create_project(args.name, args.language)

if __name__ == "__main__":
    main()
# Spiral
