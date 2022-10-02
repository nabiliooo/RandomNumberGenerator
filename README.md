/*
 * Class: CMSC203 
 * Instructor: Professor Gary Thai
 * Description: This class asks a user for an input for a random number guessing game. It will
 * prompt the user if they are too high or too low, and if they got the right answer. After,
 * it will ask if you'd like to try again.
 * Due: 10/1/2022
 * Platform/compiler: Eclipse
 * I pledge that I have completed the programming 
 * assignment independently. I have not copied the code 
 * from a student or any source. I have not given my code 
 * to any student.
   Print your Name here: Nabil El-Hage
*/
import java.util.*;

public class RandomNumberGuesser {
	public static void main(String[] args){
		
		//variables needed for the program
		RNG.resetCount();
		int randomNum = RNG.rand();
		String userTryAgain = "yes";
		int userGuess = 0;
		int lowGuess = 0;
		int highGuess = 100;
		int count = RNG.getCount();
		
		//used for later in the program, when prompted to try again
		Scanner userInput = new Scanner(System.in);
		
		//prompts user of how to use the program and asks for its first input/guess
		System.out.println("This application generates a random interger between 0 and 100"
				+ " and asks the user to guess repeatedlt until they guess correctly.");
		System.out.println("Enter your first guess: ");
		
		//gets the users guess
		userGuess = userInput.nextInt();
		
		//makes sure that the program runs properly without having the count exceeding its limit
		//and the user's guess was properly reset.
		while(count != 7 && userGuess != randomNum){
			
			//tells the user if input does not follow the given limit
			if(userGuess != randomNum) {
				RNG.inputValidation(userGuess, lowGuess, highGuess);
				
			//stores lowest number
		if(userGuess < randomNum) {
			if (userGuess > lowGuess) {
				lowGuess = userGuess;
			}
			
			//tells user their input is too low, giving another try and increasing the count
			System.out.println("Your guess is too low");
			count++;
			System.out.println("Number of guesses: " + count);
			System.out.println("Enter your next guess between " + lowGuess + " and "+ highGuess);
		
			//stores highest number
		}else if(userGuess > randomNum){
			if (userGuess < highGuess) {
				highGuess = userGuess;
			}
			
			//tells user their input is too high, giving another try and increasing the count
			System.out.println("Your guess is too high");
			count++;
			System.out.println("Number of guesses: " + count);
			System.out.println("Enter your next guess between " + lowGuess + " and "+ highGuess);
		}
		
		//asks for users next guess
		userGuess = userInput.nextInt();
			}
			
			//states the user is correct, and prompts user if they would like to try again.
			if(userGuess == randomNum) {
				count = 0;
				System.out.println("Congratulations, you guessed correctly");
				System.out.println("Try again? (yes or no)");
				userTryAgain = userInput.next();
				
				//if user says yes, it resets everything needed and program is restarted.
				//otherwise, the program is terminated.
				if (userTryAgain.equals("yes")){
					randomNum = RNG.rand();
					//System.out.println(randomNum);
					lowGuess = 0;
					highGuess = 100;
					System.out.println("Enter your first guess: ");
					userGuess = userInput.nextInt();
				}
				
			}
		}
		
		
		//if user exceeds 7 attempts, it will prompt the user and terminate the program
		if(count >= 7) {
			System.out.println("You have exceeded the maximum number of guesses, "+ count + ". Try again.");
		}
		
		//concludes program
		System.out.println("Thanks for playing...");
		System.out.println("Programmer name: Nabil El-Hage");
	}
}
