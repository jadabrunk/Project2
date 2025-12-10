# Project2
public class Project2 {
    public static void main(String[] args) {

        ArrayList<String> names = new ArrayList<>();
        ArrayList<String> firstNames = new ArrayList<>();

        try {
            // Step 1: Read names from file ito ArrayList
            File inputFile = new File("names.txt");
            Scanner fileReader = new Scanner(inputFile);

            while (fileReader.hasNextLine()) {
                String name = fileReader.nextLine().trim();
                if (!name.isEmpty()) {
                    names.add(name);
                }
            }
            fileReader.close();

            // Step 2: Sort the ArrayList in ascending order (A -> z)
            Collections.sort(names);

            // Step 3: Build second ArrayList with the first name of each letter
            char currentLetter = 'A';

            for (String name : names) {
                char firstChar = Character.toUpperCase(name.charAt(0));
                if (firstChar == currentLetter) {
                    firstNames.add(name);
                    currentLetter++;

                    if (currentLetter > 'Z') break; // stop after Z
                }
            }

            // Step 4: Sort second ArrayList in descending order (Z -> A)
            firstNames.sort(Collections.reverseOrder());

            // Step 5: Output the second list to sortednames.txt
            FileWriter writer = new FileWriter("sortednames.txt");

            for (String name : firstNames) {
                writer.write(name + "\n");
            }

            writer.close();

            System.out.println("Project 2 complete!");
            System.out.println("sortednames.txt has been created.");

        } catch (IOException e){
            System.out.println("Error: " + e.getMessage());
        }
    }
}
