---
title: "Objects and Classes in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "classes [Visual Basic]"
  - "objects [Visual Basic]"
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
caps.latest.revision: 26
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 26
---
# Objects and Classes in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

「*物件*」\(Object\) 是程式碼和資料的組合，可以視為同一單位。  物件可以是應用程式的一個片段，例如控制項或表單。  整個應用程式也可以是個物件。  
  
 當您在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中建立應用程式時，經常會使用到物件。  您可以使用 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 所提供的物件，如控制項、表單及資料存取物件 \(Data Access Object，DAO\)。  也可以在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 應用程式中使用其他應用程式的物件。  甚至可以建立自己的物件，並為該物件定義其他屬性和方法。  物件好比是預先為程式製造好的基礎材料，一段程式碼只需寫一次，即能不斷重複使用。  
  
 本主題將詳細討論物件。  
  
## 物件和類別  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中的每個物件，都是由「*類別*」\(Class\) 所定義。  類別可描述物件的變數﹑屬性﹑程序及事件。  物件是類別的執行個體，您可以在定義類別後，建立全部有需要的物件。  
  
 若要暸解物件和其類別間的關係，請想像餅乾和餅乾模型。  餅乾模型是個類別。  它定義了每片餅乾的特性︰例如，大小和形狀。  類別用來建立物件。  物件就是餅乾。  
  
 在存取物件的成員之前，您必須先建立物件。  
  
#### 從類別建立物件  
  
1.  決定要從哪一個類別建立物件。  
  
2.  撰寫 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) 來建立變數，您可以將類別執行個體指派給這個變數。  這個變數必須是所需類別的型別。  
  
    ```  
  
    Dim nextCustomer As customer   
    ```  
  
3.  加入 [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) 關鍵字，將變數初始化為類別的新執行個體。  
  
    ```  
    Dim nextCustomer As New customer  
    ```  
  
4.  現在您可以透過物件變數來存取類別的成員。  
  
    ```  
  
    nextCustomer.accountNumber = lastAccountNumber + 1  
    ```  
  
> [!NOTE]
>  您應該盡可能將變數宣告為，屬於想要將該變數指派給它的類別型別。  這就稱為「*早期繫結*」\(Early Binding\)。  如果您無法在編譯時期確認類別型別，則可以將變數宣告為 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)，以叫用「*晚期繫結*」\(Late Binding\)。  不過，晚期繫結可能會降低效能，並限制可以存取的執行階段物件成員。  如需詳細資訊，請參閱 [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)。  
  
### 多個執行個體  
 從類別新建的物件通常都相同。  然而，只要他們以個別物件形態存在，您還是可以獨立地變更其他執行個體的變數及屬性。  例如，如果您將三個核取方塊加入表單內，每個核取方塊按鈕物件就是 <xref:System.Windows.Forms.CheckBox> 類別的執行個體。  每個 <xref:System.Windows.Forms.CheckBox> 物件共用由類別所定義的通用特性和能力集合 \(屬性、變數、程序和事件\)。  但是，每個物件都有本身的名稱，可以單獨啟用和停用，還可置於表單的不同位置。  
  
## Object 成員  
 物件是應用程式的項目之一，代表類別的「*執行個體*」\(Instance\)。  欄位、屬性、方法和事件都是物件的建置組塊 \(Building Block\)，並構成物件的「*成員*」\(Member\)。  
  
### 成員存取  
 您可以依序指定物件變數的名稱、句號 \(`.`\) 和成員名稱以存取物件的成員。  下列範例會設定 <xref:System.Windows.Forms.Label> 物件的 <xref:System.Windows.Forms.Control.Text%2A> 屬性。  
  
```  
warningLabel.Text = "Data not saved"  
```  
  
#### IntelliSense 列出成員清單  
 當您叫用類別的 \[清單成員\] 選項時，IntelliSense 會列出類別的成員，例如當您輸入句號 \(`.`\) 做為成員存取運算子時。  如果您輸入句號後緊接著宣告為該類別執行個體的變數名稱，IntelliSense 就會列出所有執行個體成員，但不會列出共用成員。  如果輸入句號後緊接著類別名稱，IntelliSense 會列出所有共用成員，但不會列出執行個體成員。  如需詳細資訊，請參閱[使用 IntelliSense](/visual-studio/ide/using-intellisense)。  
  
### 欄位和屬性  
 「*欄位*」\(Field\) 和「*屬性*」\(Property\) 代表物件中儲存的資訊。  您可以使用指派陳述式擷取和設定欄位和屬性的值，方法就與擷取和設定程序中的區域變數一樣。  下列範例會擷取 <xref:System.Windows.Forms.Label> 物件的 <xref:System.Windows.Forms.Control.Width%2A> 屬性，並設定 <xref:System.Windows.Forms.Control.ForeColor%2A> 屬性。  
  
```  
Dim warningWidth As Integer = warningLabel.Width  
warningLabel.ForeColor = System.Drawing.Color.Red  
```  
  
 請注意，欄位也稱為「*成員變數*」\(Member Variable\)。  
  
 使用屬性程序的時機：  
  
-   您需要控制設定或擷取值的時機和方法。  
  
-   屬性具有定義妥善且需要加以驗證的值集。  
  
-   設定值造成可察覺的物件狀態變更，例如 `IsVisible` 屬性。  
  
-   設定屬性造成其他內部變數或其他屬性值的變更。  
  
-   在設定或擷取屬性前，必須執行一組步驟。  
  
 使用欄位的時機：  
  
-   值屬於自我驗證型別。  例如，如果將 `True` 或 `False` 以外的值指派給 `Boolean` 變數，會發生錯誤或自動資料轉換。  
  
-   資料型別所支援範圍內的任何值為有效值。  `Single` 或 `Double` 型別的許多屬性都適用。  
  
-   屬性為 `String` 資料型別，且字串大小或字串值沒有限制。  
  
-   如需詳細資訊，請參閱 [屬性程序](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)。  
  
### 方法  
 「*方法*」\(Method\) 是物件可執行的動作。  例如，<xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> 是 <xref:System.Windows.Forms.ComboBox> 物件的方法，會將新項目加入至下拉式方塊。  
  
 下列範例將示範 <xref:System.Windows.Forms.Timer> 物件的 <xref:System.Windows.Forms.Timer.Start%2A> 方法。  
  
```  
Dim safetyTimer As New System.Windows.Forms.Timer  
safetyTimer.Start()  
```  
  
 請注意，方法只是物件公開的「*程序*」\(Procedure\)。  
  
 如需詳細資訊，請參閱 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)。  
  
### 事件  
 事件是由物件所辨識的動作，如按一下滑鼠或按下按鍵，您可撰寫程式碼來回應事件。  事件可能是使用者動作或程式碼所引起的，也可能是由系統造成的。  表示事件的程式碼可「*引發*」\(Raise\) 該事件，而回應事件的程式碼則可「*處理*」\(Handle\) 事件。  
  
 您也可開發自己的自訂事件，由您的物件來引發這些事件並由其他物件來處理這些事件。  如需詳細資訊，請參閱[Events](../../../../visual-basic/programming-guide/language-features/events/events.md)。  
  
### 執行個體成員和共用成員  
 當您從類別建立物件時，即是建立該類別的執行個體。  未使用 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) 關鍵字宣告的成員是「*執行個體成員*」\(Instance Member\)，必定是屬於該特定執行個體。  執行個體中的執行個體成員，不會受到同一類別的其他執行個體中相同成員的影響。  例如，執行個體成員變數在不同的執行個體中可有不同的值。  
  
 使用 `Shared` 關鍵字宣告的成員是「*共用成員*」\(Shared Member\)，這些成員屬於整個類別而不屬於任何特定的執行個體。  無論類別建立了多少執行個體，或甚至沒有建立執行個體，共用成員只能存在一次。  例如，共用成員變數只有一個值，而可存取該類別的所有程式碼都可使用此值。  
  
#### 存取非共用成員  
  
###### 若要存取物件的非共用成員  
  
1.  確定已從類別 \(Class\) 建立物件，並且已將該物件指派給物件變數。  
  
    ```  
    Dim secondForm As New System.Windows.Forms.Form  
    ```  
  
2.  在存取成員的陳述式中，在物件變數名稱之後加上「*成員存取運算子*」\(Member\-access Operator\) \(`.`\)，然後加上成員名稱。  
  
    ```  
    secondForm.Show()  
    ```  
  
#### 存取共用成員  
  
###### 若要存取物件的共用成員  
  
-   在類別名稱之後加上「*成員存取運算子*」\(Member\-access Operator\) \(`.`\)，然後加上成員名稱。  您應該一律直接透過類別名稱來存取物件的 `Shared` 成員。  
  
    ```  
    MsgBox("This computer is called " & Environment.MachineName)  
    ```  
  
-   如果您已經從類別建立物件，則可以選擇透過物件的變數來存取 `Shared` 成員。  
  
### 類別和模組間的差異  
 類別和模組的主要差異為類別可以具現化 \(Instantiated\) 為物件，但標準模組不行。  因為標準模組資料只有一份複本，所以當程式的一部分變更了標準模組中的公用變數時，只要程式的其他部分讀取該變數時，就會取得相同的值。  相反地，每一個具現化 \(Instantiated\) 物件的物件資料會個別存在。  而另一個與標準模組不同之處是類別可以實作介面。  
  
> [!NOTE]
>  當 `Shared` 修飾詞 \(Modifier\) 套用至類別成員時，會關聯至類別本身而不是類別的特定執行個體。  使用類別名稱即可直接存取成員，與存取模組成員的方式相同。  
  
 類別和模組使用不同的成員範圍。  在類別中定義的成員位於類別中特定執行個體的範圍內，並僅於物件的存留期 \(Lifetime\) 才存在。  若要從類別外部存取類別成員，您必須使用 *Object*.*Member* 格式的完整限定名稱 \(Qualified Name\)。  
  
 另一方面，根據預設，模組內宣告的成員可公開存取，任何可存取模組的程式碼均可存取。  這表示標準模組內的公用變數是有效的全域變數，因為從專案的任何地方都是可見的，而且在程式的存留期間都會存在。  
  
## 重複使用類別和物件  
 物件可讓您單次宣告變數和程序 \(Procedure\)，之後便可在需要時重複使用。  例如，如果您想在應用程式中加入拼字檢查器，可以在應用程式中定義提供拼字檢查功能的所有變數和支援函式。  但是，如果您將拼字檢查器建立為類別，就可以在其他應用程式中加入編譯組件參考，以重複使用該拼字檢查器。  更棒的是，您還可以使用其他人開發的拼字檢查器類別，來簡化您的工作。  
  
 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] 提供許多可使用之元件的範例。  下列範例使用 <xref:System> 命名空間中的 <xref:System.TimeZone> 類別。  <xref:System.TimeZone> 提供成員，該成員可讓您擷取目前電腦系統時區的相關資訊。  
  
```  
Public Sub examineTimeZone()  
    Dim tz As System.TimeZone = System.TimeZone.CurrentTimeZone  
    Dim s As String = "Current time zone is "  
    s &= CStr(tz.GetUtcOffset(Now).Hours) & " hours and "  
    s &= CStr(tz.GetUtcOffset(Now).Minutes) & " minutes "  
    s &= "different from UTC (coordinated universal time)"  
    s &= vbCrLf & "and is currently "  
    If tz.IsDaylightSavingTime(Now) = False Then s &= "not "  
    s &= "on ""summer time""."  
    MsgBox(s)  
End Sub  
```  
  
 在上述範例中，第一個 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) 宣告型別 <xref:System.TimeZone> 的物件變數，並將 <xref:System.TimeZone.CurrentTimeZone%2A> 屬性所傳回的 <xref:System.TimeZone> 物件指定給它。  
  
## 物件關係  
 物件與其他物件關聯的方式有多種。  主要的關聯性種類有「*階層式*」\(Hierarchical\) 和「*內含項目*」\(Containment\)。  
  
### 階層式關聯性  
 當類別衍生自較為基礎的類別時，即稱它們具有「*階層式關聯性*」\(Hierarchical Relationship\)。  描述較具一般性類別的子型別項目時，類別階層架構非常有用。  
  
 在下列範例中，假設您想要定義一種特殊的 <xref:System.Windows.Forms.Button>，這個按鈕不但可像一般 <xref:System.Windows.Forms.Button> 般地使用，還會公開 \(Expose\) 方法來反轉前景色彩和背景色彩。  
  
##### 若要定義類別衍生自現有類別  
  
1.  使用 [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md) 來定義類別，您會從這個類別建立所需的物件。  
  
     `Public Class reversibleButton`  
  
     確定類別中的最後一行程式碼之後已加上 `End Class` 陳述式。  根據預設，整合式開發環境 \(IDE\) 會在您輸入 `Class` 陳述式時自動產生 `End Class`。  
  
2.  在 `Class` 陳述式之後，立即加上 [Inherits Statement](../../../../visual-basic/language-reference/statements/inherits-statement.md)。  指定衍生新類別時所根據的類別。  
  
     `Inherits System.Windows.Forms.Button`  
  
     您的新類別會繼承基底類別 \(Base Class\) 所定義的所有成員。  
  
3.  加入程式碼，以便加入其他想要讓衍生類別 \(Derived Class\) 公開 \(Expose\) 的成員。  例如，您可以加入 `reverseColors` 方法，而衍生類別 \(Derived Class\) 會有如下的外觀：  
  
    ```  
    Public Class reversibleButton  
        Inherits System.Windows.Forms.Button  
        Public Sub reverseColors()   
            Dim saveColor As System.Drawing.Color = Me.BackColor  
            Me.BackColor = Me.ForeColor  
            Me.ForeColor = saveColor  
        End Sub  
    End Class   
    ```  
  
     如果您從 `reversibleButton` 類別建立物件，則這個物件不但可以存取 <xref:System.Windows.Forms.Button> 類別的所有成員，還可以存取 `reverseColors` 方法，以及任何其他您在 `reversibleButton` 上定義的新成員。  
  
 衍生類別會從其基底類別繼承成員，讓您在類別階層架構中進行處理時可以增加複雜性。  如需詳細資訊，請參閱 [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)。  
  
#### 編譯程式碼  
 請確定編譯器 \(Compiler\) 可以存取衍生新類別時所根據的類別。  這表示您可能需要完整限定類別的名稱 \(如上述範例所示\)，或是在 [Imports Statement \(.NET Namespace and Type\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) 中辨識類別的命名空間 \(Namespace\)。  如果類別是在其他專案中，則您可能需要加入該專案的參考。  如需詳細資訊，請參閱 [管理專案中的參考](/visual-studio/ide/managing-references-in-a-project)。  
  
### 內含項目關聯性  
 另一種物件間可能彼此相關的方式稱為「*內含項目關聯性*」\(Containment Relationship\)。  容器物件在邏輯上會封裝其他的物件。  例如，<xref:System.OperatingSystem> 物件在邏輯上會包含 <xref:System.Version> 物件，這會透過其 <xref:System.OperatingSystem.Version%2A> 屬性 \(Property\) 傳回。  請注意，容器物件在實際上並沒有包含任何其他物件。  
  
#### 集合  
 「*集合*」\(Collection\) 即代表一種特殊類型的物件內含項目。  集合是可列舉的相似物件的群組。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 支援 [For Each...Next 陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) 的專用語法，讓您可以逐一查看集合中的項目。  此外，集合通常允許您使用 <xref:Microsoft.VisualBasic.Collection.Item%2A>，藉由其索引或與獨特的字串產生關聯，以擷取項目。  集合可以比陣列更容易使用，因為使用集合時，您不需使用索引即可新增或移除項目。  由於集合易於使用，因此常被用來儲存表單和控制項。  
  
## 相關主題  
 [Walkthrough: Defining Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)  
 提供建立類別的逐步說明。  
  
 [Overloaded Properties and Methods](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)  
 多載屬性和方法  
  
 [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 涵蓋繼承修飾詞、覆寫方法和屬性 MyClass 及 MyBase。  
  
 [Object Lifetime: How Objects Are Created and Destroyed](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 討論物件執行個體的建立和處置 \(Dispose\)。  
  
 [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 說明如何建立和使用匿名型別，這種型別可讓您建立物件，而不需要先撰寫資料型別的類別定義。  
  
 [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 討論物件初始設定式，物件初始設定式可透過單一運算式，用來建立具名和匿名型別的執行個體 \(Instance\)。  
  
 [如何：在匿名類型宣告中推斷屬性名稱和類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 說明如何在匿名型別宣告中推斷屬性名稱和型別。  提供成功和失敗的推斷範例。