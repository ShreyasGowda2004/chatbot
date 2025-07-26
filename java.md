Java Basics (Recap)
OOP Concepts: Inheritance, Encapsulation, Polymorphism, Abstraction

Data Types: int, float, double, char, String, boolean

Control Structures: if, for, while, switch

Collections:

List (e.g. ArrayList)

Set (e.g. HashSet)

Map (e.g. HashMap)

Streams & Lambdas: Used for functional-style operations on collections.

🧩 Spring Boot Essentials
@SpringBootApplication: Entry point of any Spring Boot app

@RestController: Used to define RESTful web services

@RequestMapping, @PostMapping, @GetMapping: Map HTTP routes

@Autowired: Inject dependencies

application.properties: External configuration (e.g. keys, URLs)

pom.xml: Manages dependencies (e.g. Spring Boot, Gson, Apache HttpClient)

📁 Common Spring Project Structure
bash
Copy
Edit
src/
├── main/
│   ├── java/
│   │   └── com/example/chatbot/
│   │       ├── config/         # API keys, constants
│   │       ├── controller/     # REST API endpoints
│   │       ├── model/          # POJOs for request/response
│   │       ├── service/        # Business logic (Gemini, GitHub)
│   │       └── AIGitChatbotApplication.java
│   └── resources/
│       └── application.properties
📦 Maven Dependency Example
Add to your pom.xml:

xml
Copy
Edit
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-web</artifactId>
</dependency>
<dependency>
  <groupId>com.google.code.gson</groupId>
  <artifactId>gson</artifactId>
  <version>2.10</version>
</dependency>
<dependency>
  <groupId>org.apache.httpcomponents.client5</groupId>
  <artifactId>httpclient5</artifactId>
  <version>5.2.1</version>
</dependency>
🤖 Gemini API (Java Usage)
You’ll use:

HttpClient or RestTemplate to send POST requests

Create JSON payload (e.g. file content → prompt → LLM)

Parse response using Gson

📦 Useful Java Libraries for AI Projects
Gson / Jackson: JSON parsing

Apache HttpClient: HTTP requests to Gemini or GitHub

JGit: Clone/read GitHub repositories programmatically

jsoup: HTML parsing if needed

🔍 1️⃣ Searching Algorithms
✅ Linear Search
Best Case (Found at start): O(1)

Worst Case: O(n)

Average Case: O(n)

java
Copy
Edit
public class LinearSearch {
    public static int linearSearch(int[] arr, int key) {
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == key) return i; // return index
        }
        return -1; // not found
    }

    public static void main(String[] args) {
        int[] arr = {5, 3, 8, 6};
        int index = linearSearch(arr, 8);
        System.out.println(index); // Output: 2
    }
}
✅ Binary Search (Array must be sorted)
Best Case: O(1)

Worst Case: O(log n)

Average Case: O(log n)

java
Copy
Edit
import java.util.Arrays;

public class BinarySearch {
    public static int binarySearch(int[] arr, int key) {
        int left = 0, right = arr.length - 1;
        while (left <= right) {
            int mid = (left + right) / 2;
            if (arr[mid] == key) return mid;
            else if (arr[mid] < key) left = mid + 1;
            else right = mid - 1;
        }
        return -1;
    }

    public static void main(String[] args) {
        int[] arr = {3, 6, 8, 12, 15};
        int index = binarySearch(arr, 8);
        System.out.println(index); // Output: 2
    }
}
🔢 2️⃣ Sorting Algorithms
Algorithm	Best Case	Average Case	Worst Case
Bubble Sort	O(n)	O(n²)	O(n²)
Selection Sort	O(n²)	O(n²)	O(n²)
Insertion Sort	O(n)	O(n²)	O(n²)
Merge Sort	O(n log n)	O(n log n)	O(n log n)
Quick Sort	O(n log n)	O(n log n)	O(n²) (rare)

🔹 Bubble Sort (O(n²))
java
Copy
Edit
public class BubbleSort {
    public static void bubbleSort(int[] arr) {
        int n = arr.length;
        for (int i = 0; i < n-1; i++) {
            for (int j = 0; j < n-i-1; j++) {
                if (arr[j] > arr[j+1]) {
                    int temp = arr[j];
                    arr[j] = arr[j+1];
                    arr[j+1] = temp;
                }
            }
        }
    }

    public static void main(String[] args) {
        int[] arr = {5, 3, 8, 6};
        bubbleSort(arr);
        for (int num : arr) System.out.print(num + " ");
    }
}
🔹 Selection Sort (O(n²))
java
Copy
Edit
public class SelectionSort {
    public static void selectionSort(int[] arr) {
        for (int i = 0; i < arr.length - 1; i++) {
            int minIdx = i;
            for (int j = i+1; j < arr.length; j++) {
                if (arr[j] < arr[minIdx]) minIdx = j;
            }
            int temp = arr[i];
            arr[i] = arr[minIdx];
            arr[minIdx] = temp;
        }
    }

    public static void main(String[] args) {
        int[] arr = {5, 3, 8, 6};
        selectionSort(arr);
        for (int num : arr) System.out.print(num + \" \");
    }
}
🔹 Insertion Sort (O(n²))
java
Copy
Edit
public class InsertionSort {
    public static void insertionSort(int[] arr) {
        for (int i = 1; i < arr.length; i++) {
            int key = arr[i];
            int j = i - 1;
            while (j >= 0 && arr[j] > key) {
                arr[j+1] = arr[j];
                j--;
            }
            arr[j+1] = key;
        }
    }

    public static void main(String[] args) {
        int[] arr = {5, 3, 8, 6};
        insertionSort(arr);
        for (int num : arr) System.out.print(num + \" \");
    }
}
🔹 Merge Sort (O(n log n))
java
Copy
Edit
public class MergeSort {
    public static void mergeSort(int[] arr, int l, int r) {
        if (l < r) {
            int mid = (l + r) / 2;
            mergeSort(arr, l, mid);
            mergeSort(arr, mid + 1, r);
            merge(arr, l, mid, r);
        }
    }

    private static void merge(int[] arr, int l, int mid, int r) {
        int n1 = mid - l + 1, n2 = r - mid;
        int[] left = new int[n1], right = new int[n2];

        for (int i = 0; i < n1; i++) left[i] = arr[l + i];
        for (int i = 0; i < n2; i++) right[i] = arr[mid + 1 + i];

        int i = 0, j = 0, k = l;
        while (i < n1 && j < n2) {
            if (left[i] <= right[j]) arr[k++] = left[i++];
            else arr[k++] = right[j++];
        }

        while (i < n1) arr[k++] = left[i++];
        while (j < n2) arr[k++] = right[j++];
    }

    public static void main(String[] args) {
        int[] arr = {5, 3, 8, 6};
        mergeSort(arr, 0, arr.length - 1);
        for (int num : arr) System.out.print(num + \" \");
    }
}
🔹 Quick Sort (O(n log n) average)
java
Copy
Edit
public class QuickSort {
    public static void quickSort(int[] arr, int low, int high) {
        if (low < high) {
            int pi = partition(arr, low, high);
            quickSort(arr, low, pi - 1);
            quickSort(arr, pi + 1, high);
        }
    }

    private static int partition(int[] arr, int low, int high) {
        int pivot = arr[high];
        int i = low - 1;
        for (int j = low; j < high; j++) {
            if (arr[j] <= pivot) {
                i++;
                int temp = arr[i]; arr[i] = arr[j]; arr[j] = temp;
            }
        }
        int temp = arr[i + 1]; arr[i + 1] = arr[high]; arr[high] = temp;
        return i + 1;
    }

    public static void main(String[] args) {
        int[] arr = {5, 3, 8, 6};
        quickSort(arr, 0, arr.length - 1);
        for (int num : arr) System.out.print(num + \" \");
    }
}

