---
title: 延後的執行範例 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: 29f118b3e6d49840b94277f17858f1339f2fb08c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61977622"
---
# <a name="deferred-execution-example-visual-basic"></a><span data-ttu-id="83578-102">延後的執行範例 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83578-102">Deferred Execution Example (Visual Basic)</span></span>
<span data-ttu-id="83578-103">本主題顯示延後執行與延遲評估如何影響您 LINQ to XML 查詢的執行。</span><span class="sxs-lookup"><span data-stu-id="83578-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83578-104">範例</span><span class="sxs-lookup"><span data-stu-id="83578-104">Example</span></span>  
 <span data-ttu-id="83578-105">下列範例顯示利用使用延後執行的擴充方法時的執行順序。</span><span class="sxs-lookup"><span data-stu-id="83578-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="83578-106">此範例會宣告三個字串的陣列。</span><span class="sxs-lookup"><span data-stu-id="83578-106">The example declares an array of three strings.</span></span> <span data-ttu-id="83578-107">接著，它會逐一查看 `ConvertCollectionToUpperCase` 所傳回的集合。</span><span class="sxs-lookup"><span data-stu-id="83578-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module Module1  
  
    <Extension()>  
    Private Iterator Function ConvertCollectionToUpperCase(  
    ByVal source As IEnumerable(Of String)) _  
    As IEnumerable(Of String)   
        For Each str As String In source  
            Console.WriteLine("ToUpper: source {0}", str)   
            Yield str.ToUpper()  
        Next  
    End Function  
  
    Sub Main()  
        Dim stringArray = New String() {"abc", "def", "ghi"}  
  
        Dim q = From str In stringArray.ConvertCollectionToUpperCase()  
                Select str  
  
        For Each Str As String In q  
            Console.WriteLine("Main: str {0}", Str)   
        Next  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="83578-108">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="83578-108">This example produces the following output:</span></span>  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="83578-109">請注意，逐一查看 `ConvertCollectionToUpperCase` 所傳回的集合時，會從來源字串陣列擷取每個項目，並在下一個項目從來源字串陣列擷取前，轉換為大寫。</span><span class="sxs-lookup"><span data-stu-id="83578-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="83578-110">您可以看到在所傳回之集合中的每個項目在 `foreach` 的 `Main` 迴圈中處理前，字串的整個陣列都沒有轉換為大寫。</span><span class="sxs-lookup"><span data-stu-id="83578-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83578-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83578-111">See also</span></span>

- [<span data-ttu-id="83578-112">教學課程：延後的執行 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83578-112">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
