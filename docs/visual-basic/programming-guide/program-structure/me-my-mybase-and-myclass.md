---
title: "Me、 My、 MyBase 和 MyClass 在 Visual Basic |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- MyClass
- vb.Me
- MyBase
- vb.MyBase
- Me
- vb.MyClass
- vb.This
- vb.My
dev_langs:
- VB
helpviewer_keywords:
- My object
- self-reference, Me keyword
- MyClass keyword, relationship to similar programming elements
- Me keyword, relationship to similar programming elements
- Me keyword, referring to the current instance of an object
- Me keyword
- self-reference
- current instance, Me keyword
- MyBase keyword, relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 59dba8961712537367db9a60e8b8ba68bcb6a1ea
ms.lasthandoff: 03/13/2017

---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Visual Basic 中的 Me、My、MyBase 和 MyClass
`Me``My`， `MyBase`，和`MyClass`中[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]有類似的名稱，但不同的用途。 本主題會描述每個實體才能區分它們。  
  
## <a name="me"></a>Me  
 `Me`關鍵字可用來參考類別或結構的程式碼目前執行所在的特定執行個體。 `Me`行為就像物件變數或目前的執行個體參考結構變數。 使用`Me`特別適用於傳遞至另一個類別、 結構或模組中的程序的類別或結構的目前執行的執行個體的相關資訊。  
  
 例如，假設您有下列的程序在模組中。  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 您可以呼叫此程序，並傳遞目前執行個體<xref:System.Windows.Forms.Form>類別做為引數使用下列陳述式。</xref:System.Windows.Forms.Form>  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>My  
 `My`功能提供簡單又直覺式存取數個[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]類別，啟用[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]使用者互動的電腦、 應用程式、 設定、 資源等。  
  
## <a name="mybase"></a>MyBase  
 `MyBase`關鍵字的行為就像參考類別的目前執行個體的基底類別的物件變數。 `MyBase`通常用來存取基底類別成員會覆寫或遮蔽衍生類別中。 `MyBase.New`用來明確地從衍生的類別建構函式呼叫基底類別建構函式。  
  
## <a name="myclass"></a>MyClass  
 `MyClass`關鍵字的行為就像原本實作類別的目前執行個體參考的物件變數。 `MyClass`類似於`Me`，但在其上的所有方法呼叫會都視為方法`NotOverridable`。  
  
## <a name="see-also"></a>另請參閱  
 [繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
