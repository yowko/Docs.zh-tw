---
title: "如何︰ 使用屬性 (Visual Basic) 建立 C + + 等位 |Microsoft 文件"
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
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3ff1686328630b233b25839c79d0009d48aab5ab
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a>如何︰ 使用屬性 (Visual Basic) 建立 C/c + + 等位
使用屬性中，您可以自訂結構在記憶體中的配置方式。 例如，您可以建立所謂的等位 C/c + + 中使用`StructLayout(LayoutKind.Explicit)`和`FieldOffset`屬性。  
  
## <a name="example"></a>範例  
 在此程式碼片段中，所有的欄位`TestUnion`在記憶體中相同的位置開始。  
  
```vb  
' Add an Imports statement for System.Runtime.InteropServices.  
  
<System.Runtime.InteropServices.StructLayout(   
      System.Runtime.InteropServices.LayoutKind.Explicit)>   
Structure TestUnion  
    <System.Runtime.InteropServices.FieldOffset(0)>   
    Public i As Integer  
  
    <System.Runtime.InteropServices.FieldOffset(0)>   
    Public d As Double  
  
    <System.Runtime.InteropServices.FieldOffset(0)>   
    Public c As Char  
  
    <System.Runtime.InteropServices.FieldOffset(0)>   
    Public b As Byte  
End Structure  
```  
  
## <a name="example"></a>範例  
 以下是另一個範例中，於不同的欄位開始明確設定位置。  
  
```vb  
' Add an Imports statement for System.Runtime.InteropServices.  
  
 <System.Runtime.InteropServices.StructLayout(   
      System.Runtime.InteropServices.LayoutKind.Explicit)>   
Structure TestExplicit  
     <System.Runtime.InteropServices.FieldOffset(0)>   
     Public lg As Long  
  
     <System.Runtime.InteropServices.FieldOffset(0)>   
     Public i1 As Integer  
  
     <System.Runtime.InteropServices.FieldOffset(4)>   
     Public i2 As Integer  
  
     <System.Runtime.InteropServices.FieldOffset(8)>   
     Public d As Double  
  
     <System.Runtime.InteropServices.FieldOffset(12)>   
     Public c As Char  
  
     <System.Runtime.InteropServices.FieldOffset(14)>   
     Public b As Byte  
 End Structure  
```  
  
 在兩個整數欄位`i1`和`i2`，共用相同的記憶體位置做為`lg`。 使用平台叫用時，這種結構配置控制項很有用。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Reflection></xref:System.Reflection>   
 <xref:System.Attribute></xref:System.Attribute>   
 [Visual Basic 程式設計指南](../../../../visual-basic/programming-guide/index.md)   
 [屬性](https://msdn.microsoft.com/library/5x6cd29c)   
 [反映 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)   
 [屬性 (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)   
 [建立自訂屬性 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)   
 [使用反映 (Visual Basic) 存取屬性](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
