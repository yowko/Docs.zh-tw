---
title: "如何︰ 查詢使用反映 (LINQ) (Visual Basic) 的組件的中繼資料 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 53caa336-ab83-4181-b0f6-5c87c5f9e4ee
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7c1bc26d7b23135dd45ad58ea0bd2510b7157448
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-query-an-assembly39s-metadata-with-reflection-linq-visual-basic"></a>如何︰ 查詢組件的中繼資料，使用反映 (LINQ) (Visual Basic)
下列範例顯示如何 LINQ 可使用反映來擷取特定的中繼資料，需符合指定的搜尋準則的方法。 在此情況下，查詢會傳回可列舉的型別，例如陣列的組件中尋找所有方法的名稱。  
  
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
  
 此範例會使用<xref:System.Reflection.Assembly.GetTypes%2A>方法來傳回型別陣列中指定的組件。</xref:System.Reflection.Assembly.GetTypes%2A> [Where 子句](../../../../visual-basic/language-reference/queries/where-clause.md)套用篩選，以便傳回只有公用型別。 針對每個公開的類型，子查詢會產生使用<xref:System.Reflection.MethodInfo>所傳回的陣列<xref:System.Type.GetMethods%2A>呼叫。</xref:System.Type.GetMethods%2A> </xref:System.Reflection.MethodInfo> 這些結果會經過篩選，傳回的傳回型別是陣列或 else 實作<xref:System.Collections.Generic.IEnumerable%601>.</xref:System.Collections.Generic.IEnumerable%601>類型的方法 最後，這些結果會依使用的型別名稱做為索引鍵。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 建立以.NET Framework 3.5 版或以上版本，搭配 system.core.dll 的參考目標的專案和`Imports`System.Linq 命名空間陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
