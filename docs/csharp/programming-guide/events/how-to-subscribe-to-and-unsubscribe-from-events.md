---
title: "如何：訂閱及取消訂閱事件 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 583168bc8cce2f4bee9a2dd35d1e59c7a0f380a6
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a>如何：訂閱及取消訂閱事件 (C# 程式設計手冊)
如果您想要撰寫在引發事件時所呼叫的自訂程式碼，您可以訂閱由其他類別發行的事件。 例如，您可以訂閱某個按鈕的 `click` 事件，讓應用程式在使用者按下該按鈕時執行某項動作。  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a>使用 Visual Studio IDE 訂閱事件  
  
1.  如果看不到 [屬性]**** 視窗，請在 [設計]**** 檢視中，以滑鼠右鍵按一下您要建立事件處理常式的表單或控制項，然後選取 [屬性]****。  
  
2.  在 [屬性]**** 視窗頂端，按一下**事件**圖示。  
  
3.  按兩下您要建立的事件，例如 `Load` 事件。  
  
     [!INCLUDE[csprcs](../../../csharp/includes/csprcs_md.md)] 會建立空的事件處理常式方法，並將其新增至您的程式碼。 您也可以在 [程式碼]**** 檢視中手動新增程式碼。 例如，下列程式碼行會宣告一個事件處理常式方法，該方法將會在 `Form` 類別引發 `Load` 事件時呼叫。  
  
     [!code-cs[csProgGuideEvents#11](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-subscribe-to-and-unsubscribe-from-events_1.cs)]  
  
     訂閱事件所需的程式碼行也會在專案之 Form1.Designer.cs 檔案的 `InitializeComponent` 方法中自動產生。 看起來像這樣：  
  
    ```  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a>以程式設計方式訂閱事件  
  
1.  定義事件處理常式方法，其簽章與事件的委派簽章相符。 例如，如果事件是以 <xref:System.EventHandler> 委派類型為基礎，則下列程式碼代表方法 Stub：  
  
    ```  
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2.  使用加法指派運算子 (`+=`) 將事件處理常式附加至事件。 在下列範例中，假設名為 `publisher` 的物件具有名為 `RaiseCustomEvent` 的事件。 請注意，subscriber 類別需要參考 publisher 類別，才能訂閱其事件。  
  
    ```  
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     請注意，以上的語法是 C# 2.0 中新增的語法。 該語法與 C# 1.0 語法完全相同，都必須使用 `new` 關鍵字明確建立封裝委派：  
  
    ```  
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     您也可以使用 Lambda 運算式新增事件處理常式：  
  
    ```  
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
        this.Click += (s,e) => { MessageBox.Show(  
           ((MouseEventArgs)e).Location.ToString());};  
    }  
    ```  
  
     如需詳細資訊，請參閱[如何：在 LINQ 之外使用 Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md)。  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a>使用匿名方法訂閱事件  
  
-   如果您稍後不需要取消訂閱事件，您可以使用加法指派運算子 (`+=`) 將匿名方法附加至事件。 在下列範例中，假設名為 `publisher` 的物件具有名為 `RaiseCustomEvent` 的事件，而且也已定義 `CustomEventArgs` 類別來包含特定類型的特製化事件資訊。 請注意，subscriber 類別需要參考 `publisher`，才能訂閱其事件。  
  
    ```  
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     請務必注意，如果使用了匿名函式訂閱事件，則無法輕易取消訂閱事件。 若要在這種情況下取消訂閱，您必須回到訂閱事件所在的程式碼，將此匿名方法儲存在委派變數中，然後將委派新增至事件。 一般而言，如果您稍後必須在程式碼中取消訂閱事件，建議您不要使用匿名函式訂閱事件。 如需匿名函式的詳細資訊，請參閱[匿名函式](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)。  
  
## <a name="unsubscribing"></a>取消訂閱  
 若要防止在引發事件時叫用事件處理常式，請取消訂閱事件。 為了避免資源流失，請先取消訂閱事件，再處置訂閱者物件。 在取消訂閱事件之前，發行物件的事件之下的多點傳送委派都會參考封裝訂閱者事件處理常式的委派。 只要發行物件還有該參考，記憶體回收就不會刪除訂閱者物件。  
  
#### <a name="to-unsubscribe-from-an-event"></a>取消訂閱事件  
  
-   使用減法指派運算子 (`-=`) 取消訂閱事件：  
  
    ```  
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     在所有訂閱者都已取消訂閱事件之後，publisher 類別中的事件執行個體會設定為 `null`。  
  
## <a name="see-also"></a>另請參閱  
 [事件](../../../csharp/programming-guide/events/index.md)   
 [event](../../../csharp/language-reference/keywords/event.md)   
 [如何：發行符合 .NET Framework 方針的事件](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)   
 [-= 運算子 (C# 參考)](../../language-reference/operators/subtraction-assignment-operator.md)   
 [+= 運算子](../../../csharp/language-reference/operators/addition-assignment-operator.md)

