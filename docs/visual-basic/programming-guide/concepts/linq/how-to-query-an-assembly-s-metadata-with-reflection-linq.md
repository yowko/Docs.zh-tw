---
title: "如何： 查詢組件 &#39; s 中繼資料，使用反映 (LINQ) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53caa336-ab83-4181-b0f6-5c87c5f9e4ee
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 718f8d78ac71c8d6d28f762e756eb2a0219fce19
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-query-an-assembly39s-metadata-with-reflection-linq-visual-basic"></a>如何： 查詢組件 &#39; s 中繼資料，使用反映 (LINQ) (Visual Basic)
下列範例示範如何搭配使用 LINQ 與反射，來擷取符合所指定搜尋準則之方法的特定中繼資料。 在此情況下，查詢會尋找組件中所有方法的名稱，而這些方法會傳回陣列這類可列舉類型。  
  
## <a name="example"></a>範例  
  
```vb  
Imports System.Reflection  
Imports System.IO  
Imports System.Linq  
Module Module1  
  
    Sub Main()  
        Dim asmbly As Assembly =   
            Assembly.Load("System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken= b77a5c561934e089")  
  
        Dim pubTypesQuery = From type In asmbly.GetTypes()   
                            Where type.IsPublic   
                            From method In type.GetMethods()   
                            Where method.ReturnType.IsArray = True   
                            Let name = method.ToString()   
                            Let typeName = type.ToString()   
                            Group name By typeName Into methodNames = Group  
  
        Console.WriteLine("Getting ready to iterate")  
        For Each item In pubTypesQuery  
            Console.WriteLine(item.methodNames)  
  
            For Each type In item.methodNames  
                Console.WriteLine(" " & type)  
            Next  
        Next  
        Console.ReadKey()  
    End Sub  
  
End Module  
```  
  
 這個範例會使用 <xref:System.Reflection.Assembly.GetTypes%2A> 方法，以傳回所指定組件中的類型陣列。 [Where 子句](../../../../visual-basic/language-reference/queries/where-clause.md)套用篩選，以便傳回只有公用型別。 對於每一個公用類型，會使用從 <xref:System.Type.GetMethods%2A> 呼叫傳回的 <xref:System.Reflection.MethodInfo> 陣列來產生子查詢。 這些結果會進行篩選，僅傳回其傳回型別為陣列的方法，或為實作 <xref:System.Collections.Generic.IEnumerable%601> 之類型的方法。 最後，會使用類型名稱作為索引鍵來群組這些結果。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 建立以 .NET Framework 3.5 版或更新版本為目標的專案，其中包含對 System.Core.dll 的參考，以及 System.Linq 命名空間的 `Imports` 陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
