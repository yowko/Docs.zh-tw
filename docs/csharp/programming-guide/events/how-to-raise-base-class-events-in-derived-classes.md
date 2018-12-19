---
title: HOW TO：在衍生類別中引發基底類別事件 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 11f34e230a1f953ba3d886e416f1ece4253e3c8d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239614"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a>HOW TO：在衍生類別中引發基底類別事件 (C# 程式設計手冊)
下列簡單的範例示範在基底類別中宣告事件的標準方式，讓事件也可以從衍生類別引發。 這個模式會在 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 類別庫的 Windows Forms 類別中廣泛使用。  
  
 當您建立可作為其他類別之基底類別的類別時，您應該考慮到事件其實是一種特殊的委派類型，只能在宣告事件的類別內予以叫用。 衍生類別無法直接叫用在基底類別內宣告的事件。 雖然有時您可能需要只能由基底類別引發的事件，但大多時候，您應該啟用衍生類別來叫用基底類別事件。 若要這樣做，您可以在包裝事件的基底類別中建立受保護的叫用方法。 藉由呼叫或覆寫這個叫用方法，衍生類別便能夠間接叫用該事件。  
  
> [!NOTE]
>  請勿在基底類別中宣告虛擬事件並在衍生類別中加以覆寫。 C# 編譯器無法正確處理這些事件，而且無法預測衍生事件的訂閱者是否會實際訂閱基底類別事件。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideEvents#1](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-raise-base-class-events-in-derived-classes_1.cs)]  
  
## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [事件](../../../csharp/programming-guide/events/index.md)  
- [委派](../../../csharp/programming-guide/delegates/index.md)  
- [存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [在 Windows Forms 中建立事件處理常式](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
