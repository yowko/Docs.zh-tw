---
title: "如何：訂閱及取消訂閱事件 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "程式碼編輯器, 事件處理常式"
  - "事件處理常式 [C#], 建立"
  - "事件 [C#], 使用 IDE 建立"
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# 如何：訂閱及取消訂閱事件 (C# 程式設計手冊)
您訂閱了某個由其他類別發行的事件，而您想要撰寫在該事件引發時呼叫的自訂程式碼。  例如，您可能訂閱了某個按鈕的 `click` 事件，好讓您的應用程式在使用者按一下該按鈕時，能夠執行某些有用的事。  
  
### 若要使用 Visual Studio IDE 訂閱事件  
  
1.  如果看不到 \[**屬性**\] 視窗，請在 \[**設計**\] 檢視中以滑鼠右鍵按一下要建立事件處理常式的表單或控制項，然後選取 \[**屬性**\]。  
  
2.  在 \[**屬性**\] 視窗的頂端，按一下 \[**事件**\] 圖示。  
  
3.  按兩下要建立的事件，例如 `Load` 事件。  
  
     [!INCLUDE[csprcs](../../../csharp/includes/csprcs-md.md)] 會建立空白的事件處理常式方法，並將其加入程式碼中。  您也可以在 \[**程式碼**\] 檢視中手動加入程式碼。  例如，下列程式碼行會宣告一個事件處理常式方法，該方法將會在 `Form` 類別引發 `Load` 事件時呼叫。  
  
     [!code-cs[csProgGuideEvents#11](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-subscribe-to-and-unsubscribe-from-events_1.cs)]  
  
     訂閱此事件所需的程式碼行也會在專案內的 Form1.Designer.cs 檔案中，於 `InitializeComponent` 方法內自動產生。  看起來像這樣：  
  
    ```  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### 若要以程式設計方式訂閱事件  
  
1.  定義事件處理常式方法，其簽章 \(Signature\) 與事件的委派簽章相符。  例如，如果該事件是以 <xref:System.EventHandler> 委派型別 \(Delegate Type\) 為基礎，則下列程式碼表示了方法 Stub：  
  
    ```  
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2.  使用加法指派運算子 \(`+=`\) 將事件處理常式附加到事件上。  在下列範例中，假設某個名為 `publisher` 的物件具有名為 `RaiseCustomEvent` 的事件。  請注意，subscriber 類別必須參考 publisher 類別，才能訂閱 publisher 類別的事件。  
  
    ```  
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     請注意，以上的語法是 C\# 2.0 中的新增語法。  這個語法與 C\# 1.0 語法完全相同，也就是必須使用 `new` 關鍵字來明確建立封裝委派：  
  
    ```  
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     這時也可以使用 Lambda 運算式來加入事件處理常式：  
  
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
  
### 若要使用匿名方法來訂閱事件  
  
-   如果您稍後不需取消訂閱事件，可以使用加法指派運算子 \(`+=`\) 將匿名方法附加至事件。  在下列範例中，假設某個名為 `publisher` 的物件具有名為 `RaiseCustomEvent`  的事件，而且也已經定義 `CustomEventArgs` 類別來包含某種特別的事件資訊。  請注意，subscriber 類別必須參考 `publisher`，才能訂閱 publisher 類別的事件。  
  
    ```  
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     請注意，如果使用了匿名函式來訂閱事件，則無法輕易取消訂閱該事件，這一點非常重要。  若要在這種情況下取消訂閱，必須回到訂閱該事件的程式碼，並將此匿名方法儲存到委派變數內，然後再將該委派加入此事件中。  一般來說，如果您在程式碼稍後必須取消訂閱事件，建議您不要使用匿名函式訂閱事件。  如需匿名函式的詳細資訊，請參閱[匿名函式](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)。  
  
## 取消訂閱  
 若要避免在引發事件時叫用 \(Invoke\) 事件處理常式，請取消訂閱該事件。  為了避免發生資源流失的情形，請務必在處置訂閱者物件之前先取消訂閱事件。  取消訂閱事件之前，發行物件內事件底層的多點傳送委派會參考封裝訂閱者之事件處理常式的委派。  只要發行物件擁有該參考，記憶體回收將無法刪除訂閱者物件。  
  
#### 若要取消訂閱事件  
  
-   使用減法指派運算子 \(`-=`\) 取消訂閱事件：  
  
    ```  
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     當所有訂閱者都取消訂閱事件時，發行者 \(Publisher\) 類別內的事件執行個體會設定為 `null`。  
  
## 請參閱  
 [事件](../../../csharp/programming-guide/events/index.md)   
 [event](../../../csharp/language-reference/keywords/event.md)   
 [如何：發行符合 .NET Framework 方針的事件](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)   
 [\-\= 運算子](../../../csharp/language-reference/operators/subtraction-assignment-operator-1.md)   
 [\+\= 運算子](../../../csharp/language-reference/operators/addition-assignment-operator.md)