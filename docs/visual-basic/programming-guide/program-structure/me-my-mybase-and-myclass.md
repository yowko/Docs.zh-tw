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
ms.openlocfilehash: a21dfeb12e8d99f5f8b8afede084846711c299ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400845"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Visual Basic 中的 Me、My、MyBase 和 MyClass
`Me`、`My``MyBase`和`MyClass`在 Visual Basic 中具有相似的名稱，但目的不同。 本主題介紹每個實體，以便區分它們。  
  
## <a name="me"></a>我  
 關鍵字`Me`提供了一種引用代碼當前正在執行的類或結構的特定實例的方法。 `Me`其活動類似于物件變數或引用當前實例的結構變數。 使用`Me`對於將有關類或結構當前執行實例的資訊傳遞給另一個類、結構或模組中的過程特別有用。  
  
 例如，假設您在模組中具有以下過程。  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 可以使用以下語句調用此過程並將<xref:System.Windows.Forms.Form>類的當前實例作為參數傳遞。  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>My  
 此功能`My`提供了對許多 .NET Framework 類的輕鬆直觀訪問，使 Visual Basic 使用者能夠與電腦、應用程式、設置、資源等進行交互。  
  
## <a name="mybase"></a>MyBase  
 關鍵字`MyBase`的作用類似于引用類當前實例的基類的物件變數。 `MyBase`通常用於訪問派生類中重寫或隱藏基類成員。 `MyBase.New`用於從派生類建構函式顯式調用基類建構函式。  
  
## <a name="myclass"></a>MyClass  
 關鍵字`MyClass`的作用類似于一個物件變數，它引用最初實現的類的當前實例。 `MyClass`與 類似`Me`，但上它的所有方法調用都被視為方法為`NotOverridable`。  
  
## <a name="see-also"></a>另請參閱

- [繼承基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
