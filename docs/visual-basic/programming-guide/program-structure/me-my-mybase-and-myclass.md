---
title: Me、My、MyBase 及 MyClass
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
ms.openlocfilehash: cc96f39d9dc37b7f1a5d8205e145869fb1b5ecef
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072232"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Visual Basic 中的 Me、My、MyBase 和 MyClass

`Me``My` `MyBase` 在 Visual Basic 中，、、和 `MyClass` 都有類似的名稱，但不同用途。 本主題將說明每個實體，以便區分它們。  
  
## <a name="me"></a>我  

 `Me`關鍵字提供一種方法，來參考程式碼目前執行所在之類別或結構的特定實例。 `Me` 的行為就像是物件變數或參考目前實例的結構變數。 在將 `Me` 目前執行中的類別或結構實例資訊傳遞給另一個類別、結構或模組中的程式時，使用特別有用。  
  
 例如，假設您在課程模組中有下列程式。  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 您可以呼叫此程式，並使用下列語句，將類別的目前實例 <xref:System.Windows.Forms.Form> 作為引數傳遞。  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>My  

 `My`這項功能可讓您輕鬆且直覺地存取許多 .NET Framework 類別，讓 Visual Basic 的使用者與電腦、應用程式、設定、資源等進行互動。  
  
## <a name="mybase"></a>MyBase  

 `MyBase`關鍵字的行為就像是參考類別目前實例之基類的物件變數。 `MyBase` 通常用來存取在衍生類別中覆寫或遮蔽的基類成員。 `MyBase.New` 用來從衍生類別的函式明確呼叫基類的函式。  
  
## <a name="myclass"></a>MyClass  

 `MyClass`關鍵字的行為就像是一種物件變數，它會參考原本所執行之類別的目前實例。 `MyClass` 類似于 `Me` ，但其上的所有方法呼叫都會視為方法 `NotOverridable` 。  
  
## <a name="see-also"></a>另請參閱

- [繼承基本概念](../language-features/objects-and-classes/inheritance-basics.md)
