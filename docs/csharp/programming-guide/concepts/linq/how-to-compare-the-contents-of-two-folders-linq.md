---
title: 如何：比較兩個資料夾的內容 (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: c7c4870e-c500-4de3-afa4-2c8e07f510e6
ms.openlocfilehash: 1517d1f9e451306e40835e6032e2aff2fe3e60ab
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44209182"
---
# <a name="how-to-compare-the-contents-of-two-folders-linq-c"></a><span data-ttu-id="5efc6-102">如何：比較兩個資料夾的內容 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="5efc6-102">How to: Compare the Contents of Two Folders (LINQ) (C#)</span></span>
<span data-ttu-id="5efc6-103">本例示範三種比較兩個檔案清單的方式︰</span><span class="sxs-lookup"><span data-stu-id="5efc6-103">This example demonstrates three ways to compare two file listings:</span></span>  
  
-   <span data-ttu-id="5efc6-104">查詢指定兩個檔案清單是否完全相同的布林值。</span><span class="sxs-lookup"><span data-stu-id="5efc6-104">By querying for a Boolean value that specifies whether the two file lists are identical.</span></span>  
  
-   <span data-ttu-id="5efc6-105">查詢交集，以擷取這兩個資料夾都有的檔案。</span><span class="sxs-lookup"><span data-stu-id="5efc6-105">By querying for the intersection to retrieve the files that are in both folders.</span></span>  
  
-   <span data-ttu-id="5efc6-106">查詢集合差異，以擷取一個資料夾中有而另一個沒有的檔案。</span><span class="sxs-lookup"><span data-stu-id="5efc6-106">By querying for the set difference to retrieve the files that are in one folder but not the other.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5efc6-107">這裡顯示的技巧可用於比較任何類型的物件序列。</span><span class="sxs-lookup"><span data-stu-id="5efc6-107">The techniques shown here can be adapted to compare sequences of objects of any type.</span></span>  
  
 <span data-ttu-id="5efc6-108">這裡顯示的 `FileComparer` 類別會示範如何一起使用自訂比較子類別和標準查詢運算子。</span><span class="sxs-lookup"><span data-stu-id="5efc6-108">The `FileComparer` class shown here demonstrates how to use a custom comparer class together with the Standard Query Operators.</span></span> <span data-ttu-id="5efc6-109">此類別不適用於實際案例。</span><span class="sxs-lookup"><span data-stu-id="5efc6-109">The class is not intended for use in real-world scenarios.</span></span> <span data-ttu-id="5efc6-110">它僅使用每個檔案以位元組計的名稱和長度，來判斷每個資料夾的內容是否相同。</span><span class="sxs-lookup"><span data-stu-id="5efc6-110">It just uses the name and length in bytes of each file to determine whether the contents of each folder are identical or not.</span></span> <span data-ttu-id="5efc6-111">在實際案例中，您應該修改此比較子以執行更嚴格的相等檢查。</span><span class="sxs-lookup"><span data-stu-id="5efc6-111">In a real-world scenario, you should modify this comparer to perform a more rigorous equality check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5efc6-112">範例</span><span class="sxs-lookup"><span data-stu-id="5efc6-112">Example</span></span>  
  
```csharp  
namespace QueryCompareTwoDirs  
{  
    class CompareDirs  
    {  
  
        static void Main(string[] args)  
        {  
  
            // Create two identical or different temporary folders   
            // on a local drive and change these file paths.  
            string pathA = @"C:\TestDir";  
            string pathB = @"C:\TestDir2";  
  
            System.IO.DirectoryInfo dir1 = new System.IO.DirectoryInfo(pathA);  
            System.IO.DirectoryInfo dir2 = new System.IO.DirectoryInfo(pathB);  
  
            // Take a snapshot of the file system.  
            IEnumerable<System.IO.FileInfo> list1 = dir1.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
            IEnumerable<System.IO.FileInfo> list2 = dir2.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
            //A custom file comparer defined below  
            FileCompare myFileCompare = new FileCompare();  
  
            // This query determines whether the two folders contain  
            // identical file lists, based on the custom file comparer  
            // that is defined in the FileCompare class.  
            // The query executes immediately because it returns a bool.  
            bool areIdentical = list1.SequenceEqual(list2, myFileCompare);  
  
            if (areIdentical == true)  
            {  
                Console.WriteLine("the two folders are the same");  
            }  
            else  
            {  
                Console.WriteLine("The two folders are not the same");  
            }  
  
            // Find the common files. It produces a sequence and doesn't   
            // execute until the foreach statement.  
            var queryCommonFiles = list1.Intersect(list2, myFileCompare);  
  
            if (queryCommonFiles.Count() > 0)  
            {  
                Console.WriteLine("The following files are in both folders:");  
                foreach (var v in queryCommonFiles)  
                {  
                    Console.WriteLine(v.FullName); //shows which items end up in result list  
                }  
            }  
            else  
            {  
                Console.WriteLine("There are no common files in the two folders.");  
            }  
  
            // Find the set difference between the two folders.  
            // For this example we only check one way.  
            var queryList1Only = (from file in list1  
                                  select file).Except(list2, myFileCompare);  
  
            Console.WriteLine("The following files are in list1 but not list2:");  
            foreach (var v in queryList1Only)  
            {  
                Console.WriteLine(v.FullName);  
            }  
  
            // Keep the console window open in debug mode.  
            Console.WriteLine("Press any key to exit.");  
            Console.ReadKey();  
        }  
    }  
  
    // This implementation defines a very simple comparison  
    // between two FileInfo objects. It only compares the name  
    // of the files being compared and their length in bytes.  
    class FileCompare : System.Collections.Generic.IEqualityComparer<System.IO.FileInfo>  
    {  
        public FileCompare() { }  
  
        public bool Equals(System.IO.FileInfo f1, System.IO.FileInfo f2)  
        {  
            return (f1.Name == f2.Name &&  
                    f1.Length == f2.Length);  
        }  
  
        // Return a hash that reflects the comparison criteria. According to the   
        // rules for IEqualityComparer<T>, if Equals is true, then the hash codes must  
        // also be equal. Because equality as defined here is a simple value equality, not  
        // reference identity, it is possible that two or more objects will produce the same  
        // hash code.  
        public int GetHashCode(System.IO.FileInfo fi)  
        {  
            string s = String.Format("{0}{1}", fi.Name, fi.Length);  
            return s.GetHashCode();  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5efc6-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="5efc6-113">Compiling the Code</span></span>  
 <span data-ttu-id="5efc6-114">建立以 .NET Framework 3.5 版或更新版本為目標的專案，該專案包含 System.Core.dll 的參考，以及 System.Linq 和 System.IO 命名空間的 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="5efc6-114">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5efc6-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="5efc6-115">See Also</span></span>

- [<span data-ttu-id="5efc6-116">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="5efc6-116">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
- [<span data-ttu-id="5efc6-117">LINQ 和檔案目錄 (C#)</span><span class="sxs-lookup"><span data-stu-id="5efc6-117">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
