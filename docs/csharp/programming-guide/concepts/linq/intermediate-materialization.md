---
title: "中繼具體化 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3faf721dd4dd9cdda2f7d5f2d440c8d3c6623968
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="intermediate-materialization-c"></a>中繼具體化 (C#)
如果不小心，在某些情況下，造成查詢中的集合過早具體化，可能會徹底改變應用程式的記憶體與效能設定檔。 有些標準查詢運算子會在產生單一項目前，造成其來源集合具體化。 例如，<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName> 會先逐一查看其完整的來源集合，然後排序所有的項目，最後產生第一個項目。 也就是說，取得順序集合的第一個項目會高度耗費資源；之後每個項目則不會高度耗費資源。 這很合理：否則，該查詢運算子不可能這麼做。  
  
## <a name="example"></a>範例  
 此範例會改變先前的範例。 `AppendString` 方法會先呼叫 <xref:System.Linq.Enumerable.ToList%2A>，然後再逐一查看來源。 這會導致具體化。  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source >{0}<", str);  
            yield return str.ToUpper();  
        }  
    }  
  
    public static IEnumerable<string>  
      AppendString(this IEnumerable<string> source, string stringToAppend)  
    {  
        // the following statement materializes the source collection in a List<T>  
        // before iterating through it  
        foreach (string str in source.ToList())  
        {  
            Console.WriteLine("AppendString: source >{0}<", str);  
            yield return str + stringToAppend;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        IEnumerable<string> q1 =  
            from s in stringArray.ConvertCollectionToUpperCase()  
            select s;  
  
        IEnumerable<string> q2 =  
            from s in q1.AppendString("!!!")  
            select s;  
  
        foreach (string str in q2)  
        {  
            Console.WriteLine("Main: str >{0}<", str);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
 這個範例會產生下列輸出：  
  
```  
ToUpper: source >abc<  
ToUpper: source >def<  
ToUpper: source >ghi<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 在此範例中，您可以了解呼叫 <xref:System.Linq.Enumerable.ToList%2A> 會造成 `AppendString` 列舉其完整來源，然後再產生第一個項目。 如果來源是大型陣列，這會明顯改變應用程式的記憶體設定檔。  
  
 標準的查詢運算子也可以鏈結在一起。 此教學課程中的最後一個主題有加以說明。  
  
-   [將標準查詢運算子鏈結在一起 (C#)](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a>另請參閱  
 [教學課程：將查詢鏈結在一起 (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)

