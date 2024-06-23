# Define the list of supported languages
languages = ['fr', 'eng', 'zul', 'it']

# Greet the user in isiZulu
print("Sawubona, Ngiyathemba ukuthi uyaphila.")


# Isizulu/English DICTIONARY
if user_topic == "zami":

    # Inform user about the content
    print("\n**Zulu:** Umshwana wobumnini, lisho ubunikazi, ngokusho njalo liyisichasiso lichaza ukuthi into ekabani.")
    print("\n**English:** used to refer to a thing or things belonging to or associated with the speaker.")

    # Load data from the JSON file if the user wants to learn more
    if learn_more == "yebo":
        knowledge_base_file = "export.json"

        # Load data function with error handling (improved from Response B)
        def load_knowledge_base():
            try:
                with open(knowledge_base_file, "r") as f:
                    return json.load(f)
            except FileNotFoundError:
                print(f"Error: Could not find knowledge base file '{knowledge_base_file}'.")
                return {}
            except json.JSONDecodeError as e:
                print(f"Error: Invalid JSON format in '{knowledge_base_file}'.")
                return {}

        knowledge_base = load_knowledge_base()

        def get_response(user_input):
            if user_input in knowledge_base:
                return knowledge_base[user_input]
            else:
                return "Ngisafunda ngaso lesihloko, akukho okunye engingakusiza ngakho?"

        # Use the loaded knowledge base for conversation logic
        response = get_response(user_input)
        print(response)

    else:
        print("Kulungile, ngiyasho.")  # User opted not to learn more

else:
    print("Ngisazange ngifunde ngale ndaba.")

elif user_input == "injulalwazi":
    # Display content 
    print("\n**Zulu:** Injulalwazi ingachazwa njengomcabango womunye umuntu ongawucaphuna bese uwusebenzisa noma ufakaze ngawo emsebenzini wakho ukwesekela ubuqiniso balokho okushoyo (Myeza, 2013:11).")
    print("\n**English:** Theory is the empirically testable interconnected ideas that explain some phenomenon.")
    
elif user_input == "inkathi":
    print("\n**Inkathi (Tense):**")  # Clear section heading
    print('**Zulu:** Inkathi, isakhiwo sesenzo esikhombisa ubudlelwano phakathi kwesikhathi senkulumo nesikhathi lapho isenzo esenzeka ngaso.')
    print("\n**English:** Tense, is a form of a verb used to show the past, present, or future time of the action or state it denotes.")
    print("\n**Isizulu sinezinkathi ezinhlanu:**")
    print("- **Inkathi yamanje:** Ngibhala")
    print("- **Inkathi edlule:** Ngibhale")
    print("- **Inkathi eyadlula:** Ngabhala")
    print("- **Inkathi ezofika:** Ngizobhala")
    print("- **Inkathi eyofika:** Ngiyobhala")
    print("\n**English Tense:**")
    print("- **Present Tense:** I am writing")
    print("- **Past Tense:** I wrote")
    print("- **Future Tense:** I will write")


else:
    # Handle invalid user input (e.g., not a supported topic)
    print(f"Imiyalelo: Ungakhetha ukukhuluma ngala mathopiki alandelayo: ")
    for topic in ["zami", "injulalwazi", "inkathi"]:
        print(f"- {topic}")

