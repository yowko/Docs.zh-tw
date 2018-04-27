---
title: Visual Basic 中的 Me、My、MyBase 和 MyClass
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
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
helpviewer_keywords:
- My object
- self-reference [Visual Basic], Me keyword
- MyClass keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], referring to the current instance of an object
- Me keyword [Visual Basic]
- self-reference
- current instance [Visual Basic], Me keyword
- MyBase keyword [Visual Basic], relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4d06c97bdf4824e878d617b2d09993d18c60336b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Visual Basic 中的 Me、My、MyBase 和 MyClass
`Me``My`， `MyBase`，和`MyClass`在 Visual Basic 中有類似的名稱，但不同的用途。 本主題會描述每個實體以加以區別。  
  
## <a name="me"></a>Me  
 `Me`關鍵字可用來參考類別或結構中的目前執行程式碼的特定執行個體。 `Me` 行為類似的物件變數或目前的執行個體參考結構變數。 使用`Me`將類別或結構的目前執行的執行個體的相關資訊傳遞至另一個類別、 結構或模組中的程序特別有用。  
  
 例如，假設您有下列程序在模組中。  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 您可以呼叫此程序，並傳遞目前的執行個體<xref:System.Windows.Forms.Form>做為引數可以使用下列陳述式的類別。  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>My  
 `My`功能可讓您容易、 淺顯易懂的存取數目[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]類別，讓 Visual Basic 使用者互動的電腦、 應用程式、 設定、 資源和等等。  
  
## <a name="mybase"></a>MyBase  
 `MyBase`關鍵字的行為就像參考目前的執行個體類別的基底類別的物件變數。 `MyBase` 通常用來存取基底類別成員會覆寫或遮蔽衍生類別中。 `MyBase.New` 用來明確地從衍生的類別建構函式呼叫的基底類別建構函式。  
  
## <a name="myclass"></a>MyClass  
 `MyClass`關鍵字的行為就像以原始實作類別的目前執行個體參考的物件變數。 `MyClass` 類似於`Me`，但其上的所有方法呼叫會都視為方法`NotOverridable`。  
  
## <a name="see-also"></a>另請參閱  
 [繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
