# codeDeploy
# Create an array with the values (1, 2, 3, 4, 5, 6, 7) and shuffle it.
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class ShuffleArray {
    public static void main(String[] args) {
  
        List<Integer> originalList = new ArrayList<>();
        originalList.add(1);
        originalList.add(2);
        originalList.add(3);
        originalList.add(4);
        originalList.add(5);
        originalList.add(6);
        originalList.add(7);

        
        Collections.shuffle(originalList);

        
        Integer[] shuffledArray = originalList.toArray(new Integer[0]);

     
        for (Integer num : shuffledArray) {
            System.out.print(num + " ");
        }
    }
}


# Enter a Roman Number as input and convert it to an integer. (Example: IX = 9)
import java.util.HashMap;
import java.util.Map;

public class RomanToInteger {
    public static int romanToInt(String s) {
       
        Map<Character, Integer> romanToInteger = new HashMap<>();
        romanToInteger.put('I', 1);
        romanToInteger.put('V', 5);
        romanToInteger.put('X', 10);
        romanToInteger.put('L', 50);
        romanToInteger.put('C', 100);
        romanToInteger.put('D', 500);
        romanToInteger.put('M', 1000);

        int result = 0;
        int prevValue = 0;

        for (int i = s.length() - 1; i >= 0; i--) {
            char currentChar = s.charAt(i);
            int currentValue = romanToInteger.get(currentChar);

            if (currentValue < prevValue) {
                result -= currentValue;
            } else {
                result += currentValue;
            }

            prevValue = currentValue;
        }

        return result;
    }

    public static void main(String[] args) {
        String romanNumeral = "X"; 
        int integerEquivalent = romanToInt(romanNumeral);
        System.out.println("The integer equivalent of " + romanNumeral + " is " + integerEquivalent);
    }
}

# Check if the input is pangram or not. (A pangram is a sentence that contains all the alphabets from A to Z)

public class PangramChecker {
    public static boolean isPangram(String input) {
        input = input.toLowerCase();
        boolean[] alphabetPresent = new boolean[26];
        for (char ch : input.toCharArray()) {
            if ('a' <= ch && ch <= 'z') {
                alphabetPresent[ch - 'a'] = true;
            }
        }

        
        for (boolean isPresent : alphabetPresent) {
            if (!isPresent) {
                return false; 
            }
        }

        return true; 
    }

    public static void main(String[] args) {
        String input = "The quick brown fox jumps over the lazy dog";
        boolean isPangram = isPangram(input);

        if (isPangram) {
            System.out.println("The input is a pangram.");
        } else {
            System.out.println("The input is not a pangram.");
        }
    }
}

# Take a sentence as an input and reverse every word in that sentence. Example - This is a sunny day > shiT si a ynnus yad.


function reverseWords(sentence) {
  
  const words = sentence.split(' ');

  
  const reversedWords = words.map(reverseWord);

  
  const reversedSentence = reversedWords.join(' ');

  return reversedSentence;
}

function reverseWord(word) {
  
  const wordArray = word.split('');

  
  const reversedArray = wordArray.reverse();

  
  return reversedArray.join('');
}

// Example usage:
const inputSentence = 'This is a sunny day in JavaScript';
const reversedSentence = reverseWords(inputSentence);

console.log('Original sentence: ' + inputSentence);
console.log('Reversed sentence: ' + reversedSentence);

# Perform sorting of an array in descending order.

function sortArrayDescending(arr) {
 return arr.sort((a, b) => {
    if (a < b) {
      return 1;
    }
    if (a > b) {
      return -1;
    }
    return 0;
 });
}

let array = [34, 56, 1, 98, 23, 54, 76, 34, 23, 76];
console.log(sortArrayDescending(array));


# Create a basic calculator using HTML, CSS, and JavaScript with the functionality of add,
subtract, multiply and divide. Use the following picture forreference


------index.html-------

<!DOCTYPE html>
<html>
<head>
    <link rel="stylesheet" type="text/css" href="style.css">
</head>
<body>
    <div class="calculator">
        <div class="display" id="display">0</div>
        <div class="buttons">
            <button onclick="clearDisplay()">C</button>
            <button onclick="appendToDisplay('7')">7</button>
            <button onclick="appendToDisplay('8')">8</button>
            <button onclick="appendToDisplay('9')">9</button>
            <button onclick="appendToDisplay('+')">+</button>
            <button onclick="appendToDisplay('4')">4</button>
            <button onclick="appendToDisplay('5')">5</button>
            <button onclick="appendToDisplay('6')">6</button>
            <button onclick="appendToDisplay('-')">-</button>
            <button onclick="appendToDisplay('1')">1</button>
            <button onclick="appendToDisplay('2')">2</button>
            <button onclick="appendToDisplay('3')">3</button>
            <button onclick="appendToDisplay('*')">*</button>
            <button onclick="appendToDisplay('0')">0</button>
            <button onclick="appendToDisplay('.')">.</button>
            <button onclick="calculate()">=</button>
            <button onclick="appendToDisplay('/')">/</button>
        </div>
    </div>
    <script src="script.js"></script>
</body>
</html>



-------style.css------
body {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
    background-color: #f2f2f2;
}

.calculator {
    background-color: #333;
    border-radius: 5px;
    width: 300px;
    text-align: right;
    padding: 10px;
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.5);
}

.display {
    font-size: 24px;
    color: #fff;
}

.buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-gap: 10px;
    margin-top: 10px;
}

button {
    font-size: 20px;
    padding: 10px;
    border: none;
    background-color: #444;
    color: #fff;
    border-radius: 5px;
    cursor: pointer;
}



-------script.js-----


let displayValue = '';

function appendToDisplay(value) {
    displayValue += value;
    document.getElementById('display').innerHTML = displayValue;
}

function clearDisplay() {
    displayValue = '';
    document.getElementById('display').innerHTML = '0';
}

function calculate() {
    try {
        displayValue = eval(displayValue);
        document.getElementById('display').innerHTML = displayValue;
    } catch (error) {
        document.getElementById('display').innerHTML = 'Error';
    }
}

# Create a survey form with Fields; First Name, Last Name, Date of Birth, Country 
(dropdown), Gender (checkbox), Profession, email, and mobile number. All the input 
fields are necessary to submit the form. Create two buttons Submit and Reset. Reset will 
reset the form while clicking on submit, first, it will check all the fields and necessary 
validations and then a popup will appear displaying all the selected values with labels in 
front of it. On closing the popup, the form should reset all the values. Use the following
image for reference

<!DOCTYPE html>
<html>
<head>
    <style>
        /* Add your CSS styles here for form layout */
    </style>
</head>
<body>
    <form id="surveyForm" onsubmit="return validateForm()">
        <label for="firstName">First Name:</label>
        <input type="text" id="firstName" required><br>

        <label for="lastName">Last Name:</label>
        <input type="text" id="lastName" required><br>

        <label for="dob">Date of Birth:</label>
        <input type="date" id="dob" required><br>

        <label for="country">Country:</label>
        <select id="country" required>
            <option value="USA">USA</option>
            <option value="Canada">Canada</option>
            <!-- Add more countries as needed -->
        </select><br>

        <label>Gender:</label><br>
        <input type="checkbox" id="male" name="gender" value="Male"> Male
        <input type="checkbox" id="female" name="gender" value="Female"> Female
        <input type="checkbox" id="other" name="gender" value="Other"> Other<br>

        <label for="profession">Profession:</label>
        <input type="text" id="profession" required><br>

        <label for="email">Email:</label>
        <input type="email" id="email" required><br>

        <label for="mobile">Mobile Number:</label>
        <input type="tel" id="mobile" required><br>

        <button type="submit" onclick="displayPopup()">Submit</button>
        <button type="button" onclick="resetForm()">Reset</button>
    </form>

    <div id="popup" class="popup">
        <span onclick="closePopup()" class="close">&times;</span>
        <h2>Form Submission</h2>
        <p>First Name: <span id="popupFirstName"></span></p>
        <p>Last Name: <span id="popupLastName"></span></p>
        <p>Date of Birth: <span id="popupDob"></span></p>
        <p>Country: <span id="popupCountry"></span></p>
        <p>Gender: <span id="popupGender"></span></p>
        <p>Profession: <span id="popupProfession"></span></p>
        <p>Email: <span id="popupEmail"></span></p>
        <p>Mobile Number: <span id="popupMobile"></span></p>
    </div>

    <script>
        function validateForm() {
            // You can add validation logic here
            return true;
        }

        function displayPopup() {
            var popup = document.getElementById("popup");
            popup.style.display = "block";

            // Retrieve form values and display them in the popup
            document.getElementById("popupFirstName").textContent = document.getElementById("firstName").value;
            document.getElementById("popupLastName").textContent = document.getElementById("lastName").value;
            document.getElementById("popupDob").textContent = document.getElementById("dob").value;
            document.getElementById("popupCountry").textContent = document.getElementById("country").value;
            
            var gender = document.querySelectorAll('input[name="gender"]:checked');
            document.getElementById("popupGender").textContent = [...gender].map(el => el.value).join(", ");

            document.getElementById("popupProfession").textContent = document.getElementById("profession").value;
            document.getElementById("popupEmail").textContent = document.getElementById("email").value;
            document.getElementById("popupMobile").textContent = document.getElementById("mobile").value;
        }

        function closePopup() {
            var popup = document.getElementById("popup");
            popup.style.display = "none";
            document.getElementById("surveyForm").reset();
        }

        function resetForm() {
            document.getElementById("surveyForm").reset();
        }
    </script>
</body>
</html>


