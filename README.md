# cs-arm

Associative Rule Mining in C#

The current project implements the Apriori algorithm for associative rule mining

Apriori algorithm is a frequent pattern mining algorithm that finds frequent patterns with support threshold defined by user.

# Install



# Usage

The [sample code](project-demo/Program.cs) below shows how to use Apriori to find the frequent item sets:

```cs 
using System;
using System.Collections.Generic;
using ARM;

namespace project_demo
{
    class Program
    {
        static void Main(string[] args)
        {
            List<HashSet<char>> database = new List<HashSet<char>>();
            database.Add(new HashSet<char>(new char[] { 'a', 'c', 'd', 'e' }));
            database.Add(new HashSet<char>(new char[] { 'a', 'b', 'e' }));
            database.Add(new HashSet<char>(new char[] { 'b', 'c', 'e' }));
            database.Add(new HashSet<char>(new char[] { 'b', 'c', 'e' }));

            Apriori<char> method = new Apriori<char>();
            Dictionary<int, List<ItemSet<char>>> itemsets = method.BuildFreqItemSet(database, new List<char>() { 'a', 'b', 'c', 'd', 'e' }, 2);
            foreach (int supportLevel in itemsets.Keys)
            {
                List<ItemSet<char>> itemsetList = itemsets[supportLevel];
                foreach (ItemSet<char> itemset in itemsetList)
                {
                    Console.WriteLine("{0} (support: {1})", itemset, itemset.SupportLevel);
                }

            }
        }
    }
}
```
