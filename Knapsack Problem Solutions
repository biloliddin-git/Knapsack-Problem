//Fractional Knapsack Problem


#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

// Structure for an item which stores weight and corresponding value of the item
struct Item {
    int profit, weight;

    // Constructor
    Item(int profit, int weight)
    {
        this->profit = profit;
        this->weight = weight;
    }
};

// Comparison function to sort items according to profit/weight ratio
static bool compareItems(struct Item a, struct Item b)
{
    double ratio1 = (double)a.profit / (double)a.weight;
    double ratio2 = (double)b.profit / (double)b.weight;
    return ratio1 > ratio2;
}

// Main greedy function to solve the problem
double fractionalKnapsack(int knapsackCapacity, vector<Item>& items)
{
    // Sorting items based on profit/weight ratio
    sort(items.begin(), items.end(), compareItems);

    double totalProfit = 0.0;

    // Looping through all items
    for (const Item& item : items) {

        // If adding the item won't overflow the knapsack, add it completely
        if (item.weight <= knapsackCapacity) {
            knapsackCapacity -= item.weight;
            totalProfit += item.profit;
        }

        // If we can't add the current item, add a fractional part of it
        else {
            totalProfit += item.profit * ((double)knapsackCapacity / (double)item.weight);
            break;
        }
    }

    // Returning the total profit
    return totalProfit;
}

int main()
{
    int numItems;
    cout << "Enter the number of items: ";
    cin >> numItems;

    vector<Item> items;
    items.reserve(numItems);

    cout << "Enter the profits and weights of the items:\n";
    for (int i = 0; i < numItems; i++)
    {
        int profit, weight;
        cout << "Item " << i + 1 << ":\n";
        cout << "Profit: ";
        cin >> profit;
        cout << "Weight: ";
        cin >> weight;
        items.emplace_back(profit, weight);
    }

    int knapsackCapacity;
    cout << "Enter the capacity of the knapsack: ";
    cin >> knapsackCapacity;

    // Function call
    cout << "Maximum profit: " << fractionalKnapsack(knapsackCapacity, items) << endl;

    return 0;
}


**************************************************************


//0-1 Knapsack Problem
#include <iostream>
using namespace std;

// A utility function that returns the maximum of two integers
int max(int a, int b) { return (a > b) ? a : b; }

// Returns the maximum value that can be put in a knapsack of capacity W
int knapSack(int knapsackCapacity, int weights[], int values[], int numItems)
{
    // Base Case
    if (numItems == 0 || knapsackCapacity == 0)
        return 0;

    // If the weight of the nth item is more than the knapsack capacity,
    // then this item cannot be included in the optimal solution
    if (weights[numItems - 1] > knapsackCapacity)
        return knapSack(knapsackCapacity, weights, values, numItems - 1);

    // Return the maximum of two cases:
    // (1) nth item included
    // (2) not included
    else
        return max(
            values[numItems - 1] + knapSack(knapsackCapacity - weights[numItems - 1], weights, values, numItems - 1),
            knapSack(knapsackCapacity, weights, values, numItems - 1));
}

int main()
{
    int numItems;
    cout << "Enter the number of items: ";
    cin >> numItems;

    int values[numItems];
    int weights[numItems];

    cout << "Enter the values of the items: ";
    for (int i = 0; i < numItems; i++)
    {
        cin >> values[i];
    }

    cout << "Enter the weights of the items: ";
    for (int i = 0; i < numItems; i++)
    {
        cin >> weights[i];
    }

    int knapsackCapacity;
    cout << "Enter the capacity of the knapsack: ";
    cin >> knapsackCapacity;

    cout << "Maximum value: " << knapSack(knapsackCapacity, weights, values, numItems) << endl;

    return 0;
}


*********************************************************************************


//0-1 Knapsack Problem, Dynamic Programming approach

#include <iostream>
using namespace std;

int knapSackRec(int knapsackCapacity, int itemWeights[], int itemValues[], int currentItem, int **dp)
{
    if (currentItem < 0)
        return 0;
    if (dp[currentItem][knapsackCapacity] != -1)
        return dp[currentItem][knapsackCapacity];

    if (itemWeights[currentItem] > knapsackCapacity)
    {
        dp[currentItem][knapsackCapacity] = knapSackRec(knapsackCapacity, itemWeights, itemValues, currentItem - 1, dp);
        return dp[currentItem][knapsackCapacity];
    }
    else
    {
        dp[currentItem][knapsackCapacity] = max(itemValues[currentItem] + knapSackRec(knapsackCapacity - itemWeights[currentItem], itemWeights, itemValues, currentItem - 1, dp),
                                                knapSackRec(knapsackCapacity, itemWeights, itemValues, currentItem - 1, dp));
        return dp[currentItem][knapsackCapacity];
    }
}

int knapSack(int knapsackCapacity, int itemWeights[], int itemValues[], int numItems)
{
    int **dp;
    dp = new int *[numItems];

    for (int i = 0; i < numItems; i++)
        dp[i] = new int[knapsackCapacity + 1];

    for (int i = 0; i < numItems; i++)
        for (int j = 0; j < knapsackCapacity + 1; j++)
            dp[i][j] = -1;

    return knapSackRec(knapsackCapacity, itemWeights, itemValues, numItems - 1, dp);
}

int main()
{
    int numItems;
    cout << "Enter the number of items: ";
    cin >> numItems;

    int itemValues[numItems];
    int itemWeights[numItems];

    cout << "Enter the values of the items: ";
    for (int i = 0; i < numItems; i++)
    {
        cin >> itemValues[i];
    }

    cout << "Enter the weights of the items: ";
    for (int i = 0; i < numItems; i++)
    {
        cin >> itemWeights[i];
    }

    int knapsackCapacity;
    cout << "Enter the capacity of the knapsack: ";
    cin >> knapsackCapacity;

    cout << "Maximum value: " << knapSack(knapsackCapacity, itemWeights, itemValues, numItems) << endl;

    return 0;
}


******************************************************************************


