---
title: "Windows Form 中的使用者輸入驗證 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "使用者輸入, 在 Windows Form 中驗證"
  - "驗證使用者輸入, Windows Form"
  - "驗證, Windows Form 使用者輸入"
  - "Windows Form, 驗證使用者輸入"
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Windows Form 中的使用者輸入驗證
當使用者將資料輸入應用程式時，您可能會想要在應用程式使用資料之前，先驗證資料是否有效。  您可能會要求某些文字欄位長度不得為零、某個欄位的格式需為電話號碼或其他語式正確 \(Well\-Formed\) 之資料型別，或是某個字串不得包含任何會危害資料庫安全性的不安全字元。  Windows Form 提供幾種方法讓您驗證應用程式的輸入。  
  
## MaskedTextBox 控制項的驗證  
 如果您需要使用者以妥善定義的格式輸入資料 \(例如電話號碼或零件編號\)，您可以使用 <xref:System.Windows.Forms.MaskedTextBox> 控制項，以最少的程式碼快速完成這項工作。  「*遮罩*」\(Mask\) 是指由遮罩語言的字元所組成的字串，這種語言會指定哪些字元可以輸入至文字方塊中的任何指定位置。  控制項會對使用者顯示一組提示。  如果使用者輸入不正確的項目 \(例如在需要數字時使用者輸入字母\)，則控制項會自動拒絕輸入。  
  
 <xref:System.Windows.Forms.MaskedTextBox> 所使用的遮罩語言非常有彈性。  可以讓您指定所需的字元、選擇性字元、常值字元 \(例如短破折號和括號\)、貨幣字元和日期分隔符號。  此控制項也可以在繫結至資料來源時順利運作。  資料繫結上的 <xref:System.Windows.Forms.Binding.Format> 事件可以用來重新格式化輸入的資料以符合遮罩，而 <xref:System.Windows.Forms.Binding.Parse> 事件則可以用來重新格式化傳出的資料，以符合資料欄位的規格。  
  
 如需詳細資訊，請參閱 [MaskedTextBox 控制項](../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md)。  
  
## 事件驅動驗證  
 如果您想對驗證進行完整的程式設計控制，或需要執行複雜的驗證檢查，您應該使用建置在大部分 Windows Form 控制項中的驗證事件。  接受自由格式的使用者輸入的每個控制項都有一個 <xref:System.Windows.Forms.Control.Validating> 事件，這個事件會在每次控制項需要資料驗證時發生。  在 <xref:System.Windows.Forms.Control.Validating> 事件處理方法中，您可以使用幾種方法驗證使用者輸入。  例如，如果文字方塊必須包含郵遞區號，您可以使用下列方式執行驗證：  
  
-   如果郵遞區號必須屬於特定群組的郵遞區號代碼，您可以對輸入執行字串比較，以驗證使用者輸入的資料。  例如，如果郵遞區號必須在 {10001, 10002, 10003} 集合中，您就可以使用字串比較驗證資料。  
  
-   如果郵遞區號必須使用特定格式，您可以使用規則運算式驗證使用者輸入的資料。  例如，若要驗證 `#####` 或 `#####-####` 格式，您可以使用 `^(\d{5})(-\d{4})?$` 規則運算式。  若要驗證 `A#A #A#` 格式，您可以使用 `[A-Z]\d[A-Z] \d[A-Z]\d` 規則運算式。  如需規則運算式的詳細資訊，請參閱 [.NET Framework 規則運算式](../../../docs/standard/base-types/regular-expressions.md)和[規則運算式範例](../../../docs/standard/base-types/regular-expression-examples.md)。  
  
-   如果郵遞區號必須是有效的美國郵遞區號代碼，您可以呼叫郵遞區號代碼 Web 服務，以驗證使用者輸入的資料。  
  
 <xref:System.Windows.Forms.Control.Validating> 事件具有一個 <xref:System.ComponentModel.CancelEventArgs> 型別的物件。  如果您判斷控制項的資料是無效的，可以將這個物件的 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> 屬性設定為 `true`，取消 <xref:System.Windows.Forms.Control.Validating> 事件。  如果您不設定 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> 屬性，Windows Form 會假設該控制項的驗證成功，並引發 <xref:System.Windows.Forms.Control.Validated> 事件。  
  
 如需在 <xref:System.Windows.Controls.TextBox> 中驗證電子郵件位址的程式碼範例，請參閱 <xref:System.Windows.Forms.Control.Validating>。  
  
### 資料繫結和事件驅動驗證  
 當您將控制項繫結至資料來源 \(例如資料表\) 時，驗證會非常有用。  您可以藉由使用驗證，確定控制項的資料符合資料來源所要求的格式，並且未包含任何特殊字元，例如可能不安全的引號和反斜線。  
  
 當您使用資料繫結時，控制項中的資料會在執行 <xref:System.Windows.Forms.Control.Validating> 事件時與資料來源同步。  如果您取消 <xref:System.Windows.Forms.Control.Validating> 事件，資料將不會與資料來源進行同步。  
  
> [!IMPORTANT]
>  如果在 <xref:System.Windows.Forms.Control.Validating> 事件後執行自訂驗證，它並不會影響資料繫結。  例如，如果在 <xref:System.Windows.Forms.Control.Validated> 事件中有嘗試取消資料繫結的程式碼，則資料繫結仍然會發生。  在上述情形中，若要在 <xref:System.Windows.Forms.Control.Validated> 事件中執行驗證，請將控制項的 \[**資料來源更新模式**\] 屬性 \(在 \[**\(資料繫結\)**\]\\\[**\(進階\)**\] 中\) 從 \[**OnValidation**\] 變更為 \[**Never**\]，並且將 *Control*`.DataBindings["`*\<YOURFIELD\>*`"].WriteValue()` 加入驗證程式碼。  
  
### 隱含和明確驗證  
 何時會驗證控制項的資料?  這個問題必須由開發人員決定。  您可以依據應用程式的需要，使用隱含或明確驗證。  
  
#### 隱含驗證  
 隱含驗證方法會在使用者輸入資料時進行驗證。  您可以在資料輸入控制項時，藉由讀取使用者按下的鍵來進行驗證，或是更常見的做法是，在使用者將輸入焦點從某個控制項移到下一個控制項時進行驗證。  當您想要對使用者正在處理的資料提供立即性回應時，這個方法就很有用。  
  
 如果您想要使用控制項的隱含驗證，就必須將該控制項的 <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> 屬性設定為 `true`。  如果您取消 <xref:System.Windows.Forms.Control.Validating> 事件，則會由指派給 <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> 的值來判斷控制項的行為。  如果您指派了 <xref:System.Windows.Forms.AutoValidate>，取消事件將造成 <xref:System.Windows.Forms.Control.Validated> 事件不會發生。  除非使用者將資料變更為有效的輸入，否則輸入焦點會保持在目前的控制項上。  如果您指派了 <xref:System.Windows.Forms.AutoValidate>，當取消事件時就不會發生 <xref:System.Windows.Forms.Control.Validated> 事件，但是焦點仍然會變更到下一個控制項。  
  
 將 <xref:System.Windows.Forms.AutoValidate> 指派給 <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> 屬性會阻止所有隱含驗證。  若要驗證控制項，您必須使用明確驗證。  
  
#### 明確驗證  
 明確驗證方法會驗證資料一次。  您可以在使用者動作的回應中驗證資料，例如按一下 \[儲存\] 按鈕或 \[下一步\] 連結。  當發生使用者動作時，您可以使用下列其中一種方法觸發明確驗證：  
  
-   呼叫 <xref:System.Windows.Forms.ContainerControl.Validate%2A>，驗證最後一個控制項是否失去焦點。  
  
-   呼叫 <xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A>，驗證表單或容器控制項中所有的子控制項。  
  
-   呼叫自訂方法，手動驗證控制項中的資料。  
  
#### Windows Form 控制項的預設隱含驗證行為  
 不同的 Windows Form 控制項對於 <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> 屬性都有不同的預設值。  下表顯示最常見的控制項及其預設值。  
  
|控制項|預設驗證行為|  
|---------|------------|  
|<xref:System.Windows.Forms.ContainerControl>|<xref:System.Windows.Forms.AutoValidate>|  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Forms.AutoValidate>|  
|<xref:System.Windows.Forms.PropertyGrid>|未在 Visual Studio 中公開的屬性|  
|<xref:System.Windows.Forms.ToolStripContainer>|未在 Visual Studio 中公開的屬性|  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Forms.AutoValidate>|  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Forms.AutoValidate>|  
  
## 關閉表單和覆寫驗證  
 當控制項所包含的資料無效而導致保留了焦點時，可以使用其中一種常用方法關閉父表單：  
  
-   按一下 \[**關閉**\] 按鈕。  
  
-   在 \[**系統**\] 功能表中選取 \[**關閉**\]。  
  
-   以程式設計方式呼叫 <xref:System.Windows.Forms.Form.Close%2A> 方法。  
  
 但是在某些情況下，無論控制項中的值是否有效，您可能想要讓使用者能夠關閉表單。  您可以為表單的 <xref:System.Windows.Forms.Form.Closing> 事件建立處理常式，以覆寫驗證，並關閉仍包含無效資料的表單。  在事件中，將 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> 屬性設定為 `false`。  如此會強制表單關閉。  如需詳細資料和範例，請參閱 <xref:System.Windows.Forms.Form.Closing?displayProperty=fullName>。  
  
> [!NOTE]
>  如果您使用這種方法強制關閉表單，表單控制項中尚未儲存的任何資料都會遺失。  此外，強制回應表單在關閉時並不會驗證控制項的內容。  您仍然可以使用控制項驗證將焦點鎖定在控制項中，但不需要考慮與關閉表單有關的行為。  
  
## 請參閱  
 <xref:System.Windows.Forms.Control.Validating?displayProperty=fullName>   
 <xref:System.Windows.Forms.Form.Closing?displayProperty=fullName>   
 <xref:System.ComponentModel.CancelEventArgs?displayProperty=fullName>   
 [MaskedTextBox 控制項](../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md)   
 [規則運算式範例](../../../docs/standard/base-types/regular-expression-examples.md)