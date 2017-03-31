---
title: "如何：使用反映查詢組件的中繼資料 (LINQ) (C#) | Microsoft Docs"
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
ms.assetid: c4cdce49-b1c8-4420-b12a-9ff7e6671368
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 50409af2add7f5ca3d591ac9d942e45ccce409af
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-query-an-assembly39s-metadata-with-reflection-linq-c"></a>如何：使用反映查詢組件的中繼資料 (LINQ) (C#)
下列範例示範如何搭配使用 LINQ 與反射，來擷取符合所指定搜尋準則之方法的特定中繼資料。 在此情況下，查詢會尋找組件中所有方法的名稱，而這些方法會傳回陣列這類可列舉類型。  
  
## <a name="example"></a>範例  
  
```csharp  
using System.Reflection;  
using System.IO;  
namespace LINQReflection  
{  
    class ReflectionHowTO  
    {  
        static void Main(string[] args)  
        {  
            Assembly assembly = Assembly.Load("System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken= b77a5c561934e089");  
            var pubTypesQuery = from type in assembly.GetTypes()  
                        where type.IsPublic  
                            from method in type.GetMethods()  
                            where method.ReturnType.IsArray == true   
                                || ( method.ReturnType.GetInterface(  
                                    typeof(System.Collections.Generic.IEnumerable<>).FullName ) != null  
                                && method.ReturnType.FullName != "System.String" )  
                            group method.ToString() by type.ToString();  
  
            foreach (var groupOfMethods in pubTypesQuery)  
            {  
                Console.WriteLine("Type: {0}", groupOfMethods.Key);  
                foreach (var method in groupOfMethods)  
                {  
                    Console.WriteLine("  {0}", method);  
                }  
            }  
  
            Console.WriteLine("Press any key to exit");  
            Console.ReadKey();  
        }  
    }    
}  
```  
  
 這個範例會使用 <xref:System.Reflection.Assembly.GetTypes%2A> 方法，來傳回所指定組件中的類型陣列。 會套用 [where](../../../../csharp/language-reference/keywords/where-clause.md) 篩選，只傳回公用類型。 針對每個公開類型，使用從 <xref:System.Type.GetMethods%2A> 呼叫所傳回的 <xref:System.Reflection.MethodInfo> 陣列來產生子查詢。 這些結果會進行篩選，僅傳回傳回型別為陣列的方法，或實作 <xref:System.Collections.Generic.IEnumerable%601> 之類型的方法。 最後，會使用類型名稱作為索引鍵來群組這些結果。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 建立以 .NET Framework 3.5 版或更高版本為目標的專案，該專案包含 System.Core.dll 的參考，以及 System.Linq 和 System.IO 命名空間的 `using` 指示詞。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
