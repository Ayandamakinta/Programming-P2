using System;
using System.Security.Cryptography.X509Certificates;
using static System.Formats.Asn1.AsnWriter;

namespace RecipeApp
{
    class Program
    {
        static void Main(string[] args)
        {
            Recipe recipe = new Recipe();
            bool exit = false;

            while (!exit)
            {
                //enter option allows the user to choosewhat part of the app they woud like to use from the 6 options provided
                Console.WriteLine("Enter option:");
                Console.WriteLine("1. Enter recipe details");
                Console.WriteLine("2. Display recipe");
                Console.WriteLine("3. Scale recipe");
                Console.WriteLine("4. Reset quantities");
                Console.WriteLine("5. Clear all data");
                Console.WriteLine("6. Exit");

                int option = int.Parse(Console.ReadLine());

                switch (option)
                {
                    case 1:
                        recipe.EnterDetails();
                        break;
                    case 2:
                        recipe.Display();
                        break;
                    case 3:
                        recipe.Scale();
                        break;
                    case 4:
                        recipe.ResetQuantities();
                        break;
                    case 5:
                        recipe = new Recipe();
                        break;
                    case 6:
                        exit = true;
                        break;
                }
            }
        }
    }

    class Recipe
    {
        private int numIngredients;
        private string[] ingredientNames;
        private double[] ingredientQuantities;
        private string[] ingredientUnits;
        private int numSteps;
        private string[] steps;

        public void EnterDetails()
        {
            // user inserts the details of the recpie
            Console.Write("Enter the number of ingredients: ");
            numIngredients = int.Parse(Console.ReadLine());

            ingredientNames = new string[numIngredients];
            ingredientQuantities = new double[numIngredients];
            ingredientUnits = new string[numIngredients];

            for (int i = 0; i < numIngredients; i++)
            {
                Console.Write($"Enter the name of ingredient {i + 1}: ");
                ingredientNames[i] = Console.ReadLine();

                Console.Write($"Enter the quantity of ingredient {i + 1}: ");
                ingredientQuantities[i] = double.Parse(Console.ReadLine());

                Console.Write($"Enter the unit of measurement of ingredient {i + 1}: ");
                ingredientUnits[i] = Console.ReadLine();
            }

            Console.Write("Enter the number of steps: ");
            numSteps = int.Parse(Console.ReadLine());

            steps = new string[numSteps];

            for (int i = 0; i < numSteps; i++)
            {
                Console.Write($"Enter step {i + 1}: ");
                steps[i] = Console.ReadLine();
            }
        }

        public void Display()
        {
            // shows the user the full recipe
            Console.WriteLine("Ingredients:");

            for (int i = 0; i < numIngredients; i++)
            {
                Console.WriteLine($"{ingredientNames[i]}: {ingredientQuantities[i]} {ingredientUnits[i]}");
            }

            Console.WriteLine("Steps:");

            for (int i = 0; i < numSteps; i++)
            {
                Console.WriteLine($"{i + 1}. {steps[i]}");
            }
        }

        public void Scale()
        {
            Console.Write("Enter scale factor (0.5, 2, or 3): ");
            double factor = double.Parse(Console.ReadLine());

            for (int i = 0; i < numIngredients; i++)
            {
                ingredientQuantities[i] *= factor;
            }
        }

        public void ResetQuantities()
        {
            //allows user to reset the quantiies to their orginal values
            for (int i = 0; i < numIngredients; i++)
            {
                ingredientQuantities[i] /= 2;

                {
                    //storing recipe information
                    
                }

            }
        }
    }
}
// Recipe class to store recipe information
public class Recipe
{
    public string Name { get; set; }
    public List<Ingredient> Ingredients { get; set; }

    public Recipe()
    {
        Ingredients = new List<Ingredient>();
    }
}
// Ingredient class to store ingredient information
 public class Ingredient
    {

        public string Name { get; set; }
        public int Calories { get; set; }
        public string FoodGroup { get; set; }
    }
public class Program

{
    private static List<Recipe> recipes = new
    List<Recipe>();
    public static void Main()
Console.WriteLine( "Welcome to the Recipe

public static void Main()
Console.WriteLine( "Welcome to the Recipe Manager!");
while (true)
Console.WriteLine("Please choose an option:");
Console.WriteLine("1. Add a recipe");
Console.WriteLine("2. View recipe list");
Console.WriteLine("3. Exit");
string option = Console.ReadLine();
switch (option)
{
case "1":
AddRecipe(); break;
case "2":
ViewRecipeList(); break;
case "3":
Console.WriteLine("Exiting the Recipe Manager. Goodbye!");
return;
default:
Console.WriteLine("Invalid option. Please try again.");
break;
}
private static void AddRecipe()

Console.WriteLine("\nAdding a new recipe...");
Recipe recipe = new Recipe();
Console.Write "Enter the recipe name: ");
while (true)
{
    Ingredient ingredient = new Ingredient();

    Console.Write("Enter ingredient name (or 'done' to finish): ");
    string ingredientName
Console.ReadLine();
    if (ingredientName.ToLower() == "done")
        break;
    ingredient.Name = ingredientName;
    Console.Write("Enter ingredient
    calories: ");
    ingredient.Calories =
    Convert.ToInt32(Console.ReadLine());
    Console.Write("Enter ingredient food group: ");
    ingredient.FoodGroup = Console.ReadLine();
    recipe.Ingredients.Add(ingredient);
}
recipes.Add(recipe);
Console.WriteLine("Recipe added successfully!");
}
private static void ViewRecipeList()
{
    Console.WriteLine("\nRecipe List:");
    if (recipes.Count == 0)
        Console.WriteLine("No recipes
        80 found.");
return;
}
List<Recipe> sortedRecipes =
84 recipes.OrderBy(r => r. Name). ToList();
foreach (Recipe recipe in sortedRecipes)
{
    Console.WriteLine("- " + recipe.Name);
}
Console.Write("Enter the name of the recipe to view: ");
string recipeName = Console.ReadLine();
Recipe selectedRecipe =
recipes.FirstOrDefault(r => r.Name == recipeName);
if (selectedRecipe != null)
    DisplayRecipe(selectedRecipe);
}
else
else
{
    Console.WriteLine("Recipe not
    100 found.'
    ");
    

    found.");
}
}
private static void DisplayRecipe(Recipe recipe)
{
    Console.WriteLine("\nRecipe: " +
    recipe.Name);
    Console.WriteLine("Ingredients:");
    foreach (Ingredient ingredient in
    109 recipe.Ingredients)
{
    Console.WriteLine("-" +
    ingredient.Name + " (" + ingredient.Calories +
    " + ingredient. FoodGroup + ")");calories,
}
int totalCalories = recipe.Ingredients.Sum(i => i.Calories);
csharp
Console.WriteLine "Total Calories: " + totalCalories);

if (totalCalories > 300)
{
    Console.WriteLine("This recipe exceeds 300 calories!");
}
}
public class RecipeManagerTests
[Test]
public void
CalculateTotalCalories ShouldReturnCorrectValue ()
Recipe recipe = new Recipe();
recipe.Ingredients.Add(new Ingredient
{
    1.Name =
"Ingredient 1",
    Calories = 100
});
recipe.Ingredients.Add(new Ingredient
{
    2.Name = "Ingredient 2",
    Calories = 200
});
int totalCalories =
14 recipe.Ingredients.Sum(i => i.Calories);
}
Assert.AreEqual(300, totalCalories);
}
