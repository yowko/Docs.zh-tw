---
title: 事件 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 4031ff08bee945f019974ad590e9b3df6d9c263c
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086228"
---
# <a name="events-c-programming-guide"></a>事件 (C# 程式設計手冊)
事件可讓 [類別](../../../csharp/language-reference/keywords/class.md) 或物件在某些相關的事情發生時，告知其他類別或物件。 傳送 (或 *「引發」*(raise)) 事件的類別稱為 *「發行者」* (publisher)，而接收 (或 *「處理」*(handle)) 事件的類別則稱為 *「訂閱者」*(subscriber)。  
  
 在典型的 C# Windows Forms 或 Web 應用程式中，您可訂閱由控制項 (如按鈕和清單方塊) 引發的事件。 您可以使用 Visual C# 整合式開發環境 (IDE) 來瀏覽控制項發行的事件，並選擇您想要處理的事件。 IDE 會自動新增空的事件處理常式方法和程式碼，以訂閱該事件。 如需詳細資訊，請參閱[如何：訂閱及取消訂閱事件](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。  
  
## <a name="events-overview"></a>事件概觀  
 事件有下列屬性：  
  
-   發行者會判斷引發事件的時間，而訂閱者則決定要採取什麼動作來回應該事件。  
  
-   一個事件可以有多個訂閱者， 而訂閱者可以處理來自多個發行者的多個事件。  
  
-   沒有訂閱者的事件永遠不會被引發。  
  
-   事件通常用於對使用者的動作 (例如在圖形化使用者介面內按一下按鈕或選取功能表) 發出信號。  
  
-   當某事件擁有多個訂閱者時，便會在事件引發的同時叫用事件處理常式。 若要以非同步方式叫用事件，請參閱 [Calling Synchronous Methods Asynchronously](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)。  
  
-   在 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 類別庫中，事件會以 <xref:System.EventHandler> 委派和 <xref:System.EventArgs> 基底類別為基礎。  
  
## <a name="related-sections"></a>相關章節  
 如需詳細資訊，請參閱:  
  
-   [如何：訂閱及取消訂閱事件](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [如何：發行符合 .NET Framework 方針的事件](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [如何：在衍生類別中引發基底類別事件](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [如何：實作介面事件](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [如何：使用字典儲存事件執行個體](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [如何：實作自訂事件存取子](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a>精選書籍章節  
 [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) (C# 3.0 Cookbook 第三版：250 個以上 C# 3.0 程式設計人員適用的方案) 中的 [Delegates, Events, and Lambda Expressions](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)  
  
 [Delegates and Events](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)  
  
## <a name="see-also"></a>請參閱

- <xref:System.EventHandler>  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [委派](../../../csharp/programming-guide/delegates/index.md)  
- [在 Windows Forms 中建立事件處理常式](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
