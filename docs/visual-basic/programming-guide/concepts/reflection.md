---
title: "反映 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3ae042933575849e105d7b681634a61319c1d6ee
ms.lasthandoff: 03/13/2017

---
# <a name="reflection-visual-basic"></a>反映 (Visual Basic)
反映提供的物件 (型別<xref:System.Type>)，描述組件、 模組和類型。</xref:System.Type> 您可以使用反映來動態建立之型別的執行個體、 繫結類型至現有的物件，或從現有的物件取得類型和叫用其方法或存取其欄位和屬性。 如果您在程式碼中使用屬性，則反映可讓您存取它們。 如需詳細資訊，請參閱[屬性](https://msdn.microsoft.com/library/5x6cd29c)。  
  
 以下是反映和使用靜態方法的簡單範例`GetType`-從所有型別繼承`Object`基底類別-若要取得變數的型別︰  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 輸出如下︰  
  
 `System.Int32`  
  
 下列範例會使用反映取得載入的組件的完整名稱。  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 輸出如下︰  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a>反映概觀  
 反映適合在下列情況︰  
  
-   當您需要存取您的程式中繼資料屬性。 如需詳細資訊，請參閱[擷取儲存於屬性中的資訊](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c)。  
  
-   檢查與組件中的型別具現化。  
  
-   建立新的型別在執行階段。 使用中<xref:System.Reflection.Emit>.</xref:System.Reflection.Emit>類別  
  
-   用於執行晚期繫結，存取執行階段建立型別的方法。 請參閱主題[動態載入和使用型別](http://msdn.microsoft.com/library/db985bec-5942-40ec-b13a-771ae98623dc)。  
  
## <a name="related-sections"></a>相關章節  
 如需詳細資訊：  
  
-   [反映](http://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775)  
  
-   [檢視類型資訊](http://msdn.microsoft.com/library/7e7303a9-4064-4738-b4e7-b75974ed70d2)  
  
-   [反映和泛用型別](http://msdn.microsoft.com/library/f7180fc5-dd41-42d4-8a8e-1b34288e06de)  
  
-   <xref:System.Reflection.Emit></xref:System.Reflection.Emit>  
  
-   [擷取儲存於屬性中的資訊](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c)  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 程式設計指南](../../../visual-basic/programming-guide/index.md)   
 [Common Language Runtime 中的組件](https://msdn.microsoft.com/library/k3677y81)
