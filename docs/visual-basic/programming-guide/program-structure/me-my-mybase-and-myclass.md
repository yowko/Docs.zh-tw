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
ms.openlocfilehash: 7df146e09a1d7cd730f4cf539d6823f7ced44bd1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002540"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Visual Basic 中的 Me、My、MyBase 和 MyClass
在 Visual Basic 中，`Me`、`My`、`MyBase` 和 `MyClass` 具有類似的名稱，但有不同的用途。 本主題將說明每個實體，以便加以區別。  
  
## <a name="me"></a>Me  
 @No__t-0 關鍵字可讓您參考目前正在執行程式碼之類別或結構的特定實例。 `Me` 的行為就像是參考目前實例的物件變數或結構變數。 使用 `Me` 特別適合用來將目前執行的類別或結構實例的相關資訊傳遞至另一個類別、結構或模組中的程式。  
  
 例如，假設您在模組中有下列程式。  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 您可以呼叫此程式，並使用下列語句，將 @no__t 0 類別的目前實例當做引數傳遞。  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>My  
 @No__t 0 功能可讓您輕鬆且直覺地存取許多 .NET Framework 類別，讓 Visual Basic 的使用者能夠與電腦、應用程式、設定、資源等進行互動。  
  
## <a name="mybase"></a>MyBase  
 @No__t-0 關鍵字的行為就像是參考類別目前實例之基類的物件變數。 `MyBase` 通常用來存取衍生類別中覆寫或陰影的基類成員。 `MyBase.New` 是用來從衍生類別的函式明確呼叫基類的「函數」（base class）。  
  
## <a name="myclass"></a>MyClass  
 @No__t-0 關鍵字的行為就像是物件變數，其參考原本實作為之類別的目前實例。 `MyClass` 類似于 `Me`，但其上的所有方法呼叫都會視為方法已 `NotOverridable`。  
  
## <a name="see-also"></a>另請參閱

- [繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
