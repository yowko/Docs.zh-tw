---
title: 使用者輸入驗證
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, validating user input
- validation [Windows Forms], Windows Forms user input
- user input [Windows Forms], validating in Windows Forms
- validating user input [Windows Forms], Windows Forms
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
ms.openlocfilehash: eafbf54552566011fef9d2dbeb5e9f9fa3facabd
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646307"
---
# <a name="user-input-validation-in-windows-forms"></a>Windows Form 中的使用者輸入驗證
當使用者在應用程式中輸入數據時,您可能希望在應用程式使用數據之前驗證數據是否有效。 您可以要求某些文字欄位不是零長度,欄位必須格式化為電話號碼或其他類型的格式良好的資料,或者字串不包含任何可能用於危害資料庫安全性的不安全字元。 Windows 表單提供測試應用程式中輸入的方法。  
  
## <a name="validation-with-the-maskedtextbox-control"></a>使用遮罩  
 如果需要要求使用者以定義良好的格式(如電話號碼或部件號)輸入數據,則可以使用<xref:System.Windows.Forms.MaskedTextBox>控制項快速且使用最少的代碼完成此任務。 *蒙版*是由掩蔽語言中的字元組成的字串,用於指定可以在文本框中的任何給定位置輸入哪些字元。 該控件向用戶顯示一組提示。 如果用戶鍵入不正確的條目,例如,當使用者在需要數位時鍵入字母,控件將自動拒絕輸入。  
  
 所使用的掩蔽語言<xref:System.Windows.Forms.MaskedTextBox>非常靈活。 它允許您指定所需的字元、可選字元、字面字元(如連字元和括弧、貨幣字元和日期分隔符)。 綁定到數據源時,該控件也工作正常。 數據<xref:System.Windows.Forms.Binding.Format>綁定上的事件可用於重格式化傳入數據以符合掩碼,<xref:System.Windows.Forms.Binding.Parse>該事件可用於重格式化傳出數據以符合數據欄位的規範。  
  
 關於詳細資訊,請參閱[影像文字盒控制 。](./controls/maskedtextbox-control-windows-forms.md)  
  
## <a name="event-driven-validation"></a>事件驅動驗證  
 如果要對驗證進行完全程式設計控制,或者需要執行複雜的驗證檢查,則應使用大多數 Windows 窗體控制項中內置的驗證事件。 接受自由格式使用者輸入的每個控制項都有一個<xref:System.Windows.Forms.Control.Validating>事件,該事件將在控制項需要數據驗證時發生。 在<xref:System.Windows.Forms.Control.Validating>事件處理方法中,您可以通過多種方式驗證使用者輸入。 例如,如果您有一個必須包含郵遞區編碼的文本框,則可以通過以下方式執行驗證:  
  
- 如果郵政編碼必須屬於特定的郵政編碼組,則可以對輸入執行字串比較,以驗證使用者輸入的數據。 例如,如果郵政編碼必須位於集 {10001、10002、10003}中,則可以使用字串比較來驗證數據。  
  
- 如果郵政編碼必須採用特定形式,則可以使用正則表達式來驗證使用者輸入的數據。 例如,要驗證窗體`#####``#####-####`或 ,可以使用正規表示`^(\d{5})(-\d{4})?$`式 。 要驗證表單`A#A #A#`,可以使用正規表示式`[A-Z]\d[A-Z] \d[A-Z]\d`。 有關正規表示式的詳細資訊,請參閱[.NET 框架正規表示式](../../standard/base-types/regular-expressions.md)與[正規表示式範例](../../standard/base-types/regular-expression-example-scanning-for-hrefs.md)。  
  
- 如果郵政編碼必須是有效的美國郵政編碼,您可以調用郵政編碼 Web 服務來驗證使用者輸入的數據。  
  
 事件<xref:System.Windows.Forms.Control.Validating>提供類型的<xref:System.ComponentModel.CancelEventArgs>物件 。 如果確定控制項的數據無效,則可以通過將此物件的<xref:System.Windows.Forms.Control.Validating><xref:System.ComponentModel.CancelEventArgs.Cancel%2A>屬性`true`設置為取消事件。 如果不設置屬性,Windows<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>窗體將假定該控件的驗證成功,並引發<xref:System.Windows.Forms.Control.Validated>該 事件。  
  
 認證的電子郵件地址的代碼範例,<xref:System.Windows.Controls.TextBox>請參考<xref:System.Windows.Forms.Control.Validating>。  
  
### <a name="data-binding-and-event-driven-validation"></a>資料繫結和事件驅動驗證  
 當您將控制項裝置綁定到資料來源(如資料庫表)時,驗證非常有用。 通過使用驗證,可以確保控件的數據滿足數據來源所需的格式,並且不包含任何可能不安全的特殊字元,如引號和斜杠。  
  
 使用數據綁定時,控件中的數據在執行<xref:System.Windows.Forms.Control.Validating>事件期間會與數據源同步。 如果取消該<xref:System.Windows.Forms.Control.Validating>事件,數據將不會與數據源同步。  
  
> [!IMPORTANT]
> 如果<xref:System.Windows.Forms.Control.Validating>具有在事件發生後進行的自定義驗證,則不會影響數據綁定。 例如,如果<xref:System.Windows.Forms.Control.Validated>嘗試取消數據綁定的事件有代碼,則數據綁定仍將發生。 在這種情況下,要<xref:System.Windows.Forms.Control.Validated>在事件中執行驗證,請將控制項的**資料來源更新模式**屬性(**下(資料綁定)(**\\**進階)** 從**On 驗證**更改為**從不**,並將*控制*`.DataBindings["`*\<YOURFIELD>*`"].WriteValue()`添加到驗證代碼中。  
  
### <a name="implicit-and-explicit-validation"></a>隱含及繪圖型驗證  
 那麼,控件的數據何時得到驗證? 這由您,開發人員決定。 您可以根據應用程式的需求使用隱式或顯式驗證。  
  
#### <a name="implicit-validation"></a>隱式驗證  
 隱式驗證方法在使用者輸入數據時驗證數據。 通過在按鍵時讀取數據輸入數據時驗證數據,或者當使用者將輸入焦點從一個控制項移開並移動到下一個控制項時,更常見的驗證數據。 當您希望向使用者提供有關數據工作時的即時反饋時,此方法非常有用。  
  
 如果要對控制項使用隱式驗證,則必須將該控制項的屬性<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>設定<xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange>為<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>或 。 如果取消此<xref:System.Windows.Forms.Control.Validating>事件,控制項的行為將由分配給的值<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>決定 。 如果分配<xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange>,取消事件將<xref:System.Windows.Forms.Control.Validated>導致 事件不會發生。 輸入焦點將保留在當前控制項上,直到使用者將資料更改為有效輸入。 如果分配<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>了<xref:System.Windows.Forms.Control.Validated>,則取消事件時不會發生事件,但焦點仍將更改為下一個控件。  
  
 分配給<xref:System.Windows.Forms.AutoValidate.Disable><xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>屬性 可完全防止隱式驗證。 要驗證控件,必須使用顯式驗證。  
  
#### <a name="explicit-validation"></a>明確驗證  
 顯式驗證方法一次驗證數據。 您可以驗證數據以回應使用者操作,例如按一下「儲存」按鈕或「下一步」連結。 發生使用者操作時,可以通過以下方式之一觸發顯式驗證:  
  
- 調用<xref:System.Windows.Forms.ContainerControl.Validate%2A>以驗證最後一個控件失去焦點。  
  
- 呼叫<xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A>以驗證表單或容器控制件中的所有子控制件。  
  
- 調用自定義方法以手動驗證控制項中的數據。  
  
#### <a name="default-implicit-validation-behavior-for-windows-forms-controls"></a>Windows 表單控制項的預設隱式驗證行為  
 不同的 Windows 窗體控<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>件對其 屬性具有不同的預設值。 下表顯示了最常見的控制件及其預設值。  
  
|控制|預設驗證行為|  
|-------------|---------------------------------|  
|<xref:System.Windows.Forms.ContainerControl>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
|<xref:System.Windows.Forms.PropertyGrid>|未在視覺工作室中公開的屬性|  
|<xref:System.Windows.Forms.ToolStripContainer>|未在視覺工作室中公開的屬性|  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
  
## <a name="closing-the-form-and-overriding-validation"></a>關閉表單與覆寫驗證  
 當控件由於它包含的資料無效而保持焦點時,不可能以通常的方式之一關閉父窗體:  
  
- 通過按下 **「關閉**」按鈕。  
  
- 通過在 **「系統**」功能表中選擇 **「關閉**」。  
  
- 通過以程式設計<xref:System.Windows.Forms.Form.Close%2A>方式調用方法。  
  
 但是,在某些情況下,您可能希望讓使用者關閉窗體,而不管控件中的值是否有效。 您可以透過為表<xref:System.Windows.Forms.Form.FormClosing>單的事件建立處理程式來覆蓋驗證並關閉仍包含無效資料的表單。 在這種情況下,將<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>屬性設定`false`為 。 這將強制窗體關閉。 如需詳細資訊和範例，請參閱 <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>。  
  
> [!NOTE]
> 如果強制以這種方式關閉窗體,則窗體控件中尚未保存的任何數據都將丟失。 此外,模態窗體在關閉控制項時不會驗證它們的內容。 您仍可以使用控制項驗證將焦點鎖定到控制項,但不必擔心與關閉窗體相關的行為。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Control.Validating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>
- <xref:System.Windows.Forms.FormClosingEventArgs?displayProperty=nameWithType>
- [MaskedTextBox 控制項](./controls/maskedtextbox-control-windows-forms.md)
- [規則運算式範例](../../standard/base-types/regular-expression-example-scanning-for-hrefs.md)
