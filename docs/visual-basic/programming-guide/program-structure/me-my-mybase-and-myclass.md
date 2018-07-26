---
title: Visual Basic 中的 Me、My、MyBase 和 MyClass
ms.date: 07/20/2015
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
ms.openlocfilehash: f3db5f8f6688e68992f683ac1b1465078aa41231
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244708"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Visual Basic 中的 Me、My、MyBase 和 MyClass
`Me``My`， `MyBase`，和`MyClass`Visual Basic 中有類似的名稱，但不同的用途。 本主題會描述每個實體以區別。  
  
## <a name="me"></a>Me  
 `Me`關鍵字可用來參考類別或結構的程式碼目前執行所在的特定執行個體。 `Me` 物件變數或目前的執行個體參考結構變數等的行為。 使用`Me`特別適用於將目前執行的執行個體的類別或結構的相關資訊傳遞至另一個類別、 結構或模組中的程序。  
  
 例如，假設您有在模組中的下列程序。  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 您可以呼叫此程序，並傳遞目前的執行個體<xref:System.Windows.Forms.Form>做為引數使用下列陳述式的類別。  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>My  
 `My`功能提供簡單又直覺式存取數個[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]類別，讓 Visual Basic 使用者與電腦、 應用程式、 設定、 資源等等互動。  
  
## <a name="mybase"></a>MyBase  
 `MyBase`關鍵字的行為就像參考類別的目前執行個體的基底類別的物件變數。 `MyBase` 通常用來存取所覆寫或遮蔽衍生類別中的基底類別成員。 `MyBase.New` 用來明確地從衍生的類別建構函式呼叫的基底類別建構函式。  
  
## <a name="myclass"></a>MyClass  
 `MyClass`關鍵字的行為就像參考目前的執行個體的類別，以原始實作的物件變數。 `MyClass` 類似於`Me`，但在其上的所有方法呼叫會都視為方法`NotOverridable`。  
  
## <a name="see-also"></a>另請參閱  
 [繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
