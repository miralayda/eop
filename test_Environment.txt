import os

FILENAME = 'ab environment.txt'


def save_file(prompt):
    '''Takes current environment directory and write in text'''
    saving_dir = os.getcwd()
    with open(FILENAME, 'w', encoding='UTF-8') as file_out:
        file_out.write(f'{prompt}: {saving_dir}\n')


def read_file():
    '''Reads text file contents'''
    with open(FILENAME, 'r') as file_in:
        contents = file_in.read()
    print(contents)


def change_directory():

    current_dir = os.getcwd()
    print('\nCurrent Root Directory of your environment')
    save_file('Main directory')
    read_file()
    print('CREATING "in main" folder in environment')
    create_folder_name = 'a main'
    folder_path = os.path.join(current_dir, create_folder_name)
    if not os.path.exists(folder_path):
        os.makedirs(folder_path)
    os.chdir(folder_path)
    save_file('Changed directory')
    read_file()
    print('DONE')


change_directory()
