---
title: '如何在衍生類別中引發基類事件-c # 程式設計手冊'
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: e2d2dfc2809a4de1756bfc362880eebc79076b94
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240626"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="4c961-102">如何在衍生類別中引發基類事件（c # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="4c961-102">How to raise base class events in derived classes (C# Programming Guide)</span></span>
<span data-ttu-id="4c961-103">下列簡單的範例示範在基底類別中宣告事件的標準方式，讓事件也可以從衍生類別引發。</span><span class="sxs-lookup"><span data-stu-id="4c961-103">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="4c961-104">此模式廣泛用於 .NET 類別庫中的 Windows Forms 類別。</span><span class="sxs-lookup"><span data-stu-id="4c961-104">This pattern is used extensively in Windows Forms classes in the .NET class libraries.</span></span>  
  
 <span data-ttu-id="4c961-105">當您建立可作為其他類別之基底類別的類別時，您應該考慮到事件其實是一種特殊的委派類型，只能在宣告事件的類別內予以叫用。</span><span class="sxs-lookup"><span data-stu-id="4c961-105">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="4c961-106">衍生類別無法直接叫用在基底類別內宣告的事件。</span><span class="sxs-lookup"><span data-stu-id="4c961-106">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="4c961-107">雖然有時您可能需要只能由基底類別引發的事件，但大多時候，您應該啟用衍生類別來叫用基底類別事件。</span><span class="sxs-lookup"><span data-stu-id="4c961-107">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="4c961-108">若要這樣做，您可以在包裝事件的基底類別中建立受保護的叫用方法。</span><span class="sxs-lookup"><span data-stu-id="4c961-108">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="4c961-109">藉由呼叫或覆寫這個叫用方法，衍生類別便能夠間接叫用該事件。</span><span class="sxs-lookup"><span data-stu-id="4c961-109">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4c961-110">請勿在基底類別中宣告虛擬事件並在衍生類別中加以覆寫。</span><span class="sxs-lookup"><span data-stu-id="4c961-110">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="4c961-111">C# 編譯器無法正確處理這些事件，而且無法預測衍生事件的訂閱者是否會實際訂閱基底類別事件。</span><span class="sxs-lookup"><span data-stu-id="4c961-111">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c961-112">範例</span><span class="sxs-lookup"><span data-stu-id="4c961-112">Example</span></span>  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4c961-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c961-113">See also</span></span>

- [<span data-ttu-id="4c961-114">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="4c961-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4c961-115">事件</span><span class="sxs-lookup"><span data-stu-id="4c961-115">Events</span></span>](./index.md)
- [<span data-ttu-id="4c961-116">委派</span><span class="sxs-lookup"><span data-stu-id="4c961-116">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="4c961-117">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="4c961-117">Access Modifiers</span></span>](../classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="4c961-118">在 Windows Form 中建立事件處理常式</span><span class="sxs-lookup"><span data-stu-id="4c961-118">Creating Event Handlers in Windows Forms</span></span>](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
