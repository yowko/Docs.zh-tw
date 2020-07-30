---
title: '如何在衍生類別中引發基類事件-c # 程式設計手冊'
description: 瞭解如何在衍生類別中引發基類事件。 查看程式碼範例，並查看其他可用的資源。
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: b0b0a16a1fd165e437fc79ccacb20d406f5cff63
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302096"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a>如何在衍生類別中引發基類事件（c # 程式設計手冊）
下列簡單的範例示範在基底類別中宣告事件的標準方式，讓事件也可以從衍生類別引發。 此模式廣泛用於 .NET 類別庫中的 Windows Forms 類別。  
  
 當您建立可作為其他類別之基底類別的類別時，您應該考慮到事件其實是一種特殊的委派類型，只能在宣告事件的類別內予以叫用。 衍生類別無法直接叫用在基底類別內宣告的事件。 雖然有時您可能需要只能由基底類別引發的事件，但大多時候，您應該啟用衍生類別來叫用基底類別事件。 若要這樣做，您可以在包裝事件的基底類別中建立受保護的叫用方法。 藉由呼叫或覆寫這個叫用方法，衍生類別便能夠間接叫用該事件。  
  
> [!NOTE]
> 請勿在基底類別中宣告虛擬事件並在衍生類別中加以覆寫。 C# 編譯器無法正確處理這些事件，而且無法預測衍生事件的訂閱者是否會實際訂閱基底類別事件。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)
- [事件](./index.md)
- [委派](../delegates/index.md)
- [存取修飾詞](../classes-and-structs/access-modifiers.md)
- [在 Windows Form 中建立事件處理常式](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
