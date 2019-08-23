---
title: Windows Form 中的使用者輸入驗證
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, validating user input
- validation [Windows Forms], Windows Forms user input
- user input [Windows Forms], validating in Windows Forms
- validating user input [Windows Forms], Windows Forms
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
ms.openlocfilehash: 0a1d6c4c18e658d71f1baf90763e121314ea35d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916299"
---
# <a name="user-input-validation-in-windows-forms"></a>Windows Form 中的使用者輸入驗證
當使用者在您的應用程式中輸入資料時, 您可能會想要在應用程式使用資料之前先驗證其是否有效。 您可能需要某些文字欄位不是長度為零、欄位要格式化為電話號碼或其他類型的格式正確的資料, 或字串未包含任何可能用來危害資料庫安全性的不安全字元。 Windows Forms 提供數種方式, 讓您在應用程式中驗證輸入。  
  
## <a name="validation-with-the-maskedtextbox-control"></a>使用 MaskedTextBox 控制項進行驗證  
 如果您需要讓使用者以妥善定義的格式 (例如電話號碼或元件編號) 輸入資料, 可以使用<xref:System.Windows.Forms.MaskedTextBox>控制項快速完成這項工作, 並使用最少的程式碼。 *遮罩*是由遮罩語言中的字元所組成的字串, 可指定要在文字方塊中的任何指定位置輸入哪些字元。 控制項會向使用者顯示一組提示。 如果使用者輸入不正確的專案 (例如, 使用者在需要數位時鍵入字母), 控制項會自動拒絕輸入。  
  
 使用的遮罩語言非常<xref:System.Windows.Forms.MaskedTextBox>有彈性。 它可讓您指定必要的字元、選擇性字元、常值字元, 例如連字號和括弧、貨幣字元和日期分隔符號。 當系結至資料來源時, 控制項也能正常運作。 資料<xref:System.Windows.Forms.Binding.Format>系結上的事件可以用來重新格式化傳入資料以符合遮罩, <xref:System.Windows.Forms.Binding.Parse>而事件可用來重新格式化傳出資料, 以符合資料欄位的規格。  
  
 如需詳細資訊, 請參閱[MaskedTextBox Control](./controls/maskedtextbox-control-windows-forms.md)。  
  
## <a name="event-driven-validation"></a>事件驅動驗證  
 如果您想要完全以程式設計方式控制驗證, 或需要執行複雜的驗證檢查, 您應該使用大部分 Windows Forms 控制項內建的驗證事件。 接受自由形式使用者輸入的每個控制項都有<xref:System.Windows.Forms.Control.Validating>一個事件, 每當控制項需要進行資料驗證時, 就會發生這種情況。 <xref:System.Windows.Forms.Control.Validating>在事件處理方法中, 您可以透過數種方式來驗證使用者輸入。 例如, 如果您有一個必須包含郵遞區號的文字方塊, 您可以利用下列方式來執行驗證:  
  
- 如果郵遞區號必須屬於特定的 zip 代碼群組, 您可以對輸入執行字串比較, 以驗證使用者輸入的資料。 例如, 如果郵遞區號必須位於 {10001, 10002, 10003} 的集合中, 則您可以使用字串比較來驗證資料。  
  
- 如果郵遞區號必須是特定的表單, 您可以使用正則運算式來驗證使用者所輸入的資料。 例如, 若要驗證表單`#####`或`#####-####`, 您可以使用正則運算式`^(\d{5})(-\d{4})?$`。 若要驗證窗`A#A #A#`體, 您可以使用正則`[A-Z]\d[A-Z] \d[A-Z]\d`運算式。 如需正則運算式的詳細資訊, 請參閱[.NET Framework 正則運算式](../../standard/base-types/regular-expressions.md)和[正則運算式範例](../../standard/base-types/regular-expression-examples.md)。  
  
- 如果郵遞區號必須是有效的美國郵遞區號, 您可以呼叫 Zip 代碼 Web 服務來驗證使用者所輸入的資料。  
  
 系統會提供類型<xref:System.ComponentModel.CancelEventArgs>的物件給事件。<xref:System.Windows.Forms.Control.Validating> 如果您判斷控制項的資料無效, 可以將此物件的<xref:System.Windows.Forms.Control.Validating> <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>屬性設定為, 以`true`取消該事件。 如果您未設定<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>屬性, Windows Forms 會假設該控制項的驗證成功, 並<xref:System.Windows.Forms.Control.Validated>引發事件。  
  
 如需在中<xref:System.Windows.Controls.TextBox>驗證電子郵件地址的程式碼範例, 請參閱。 <xref:System.Windows.Forms.Control.Validating>  
  
### <a name="data-binding-and-event-driven-validation"></a>資料系結和事件驅動驗證  
 當您將控制項系結至資料來源 (例如資料庫資料表) 時, 驗證會非常有用。 藉由使用驗證, 您可以確定控制項的資料符合資料來源所需的格式, 而且不包含任何特殊字元, 例如引號和反斜線可能不安全。  
  
 當您使用資料系結時, 控制項中的資料會在<xref:System.Windows.Forms.Control.Validating>事件執行期間與資料來源同步處理。 如果您取消<xref:System.Windows.Forms.Control.Validating>事件, 資料將不會與資料來源同步處理。  
  
> [!IMPORTANT]
> 如果您有在<xref:System.Windows.Forms.Control.Validating>事件之後發生的自訂驗證, 則不會影響資料系結。 例如, 如果您的程式碼<xref:System.Windows.Forms.Control.Validated>嘗試取消資料系結, 則資料系結仍然會發生。 在此情況下<xref:System.Windows.Forms.Control.Validated> , 若要在事件中執行驗證, 請將控制項的**資料來源更新模式**屬性 (**在 [(** \\資料系結)] 底下) 從**OnValidation**變更為 [**從不**], 然後新增*控制*`.DataBindings["` YOURFIELD>`"].WriteValue()`您的驗證程式代碼。 *\<*  
  
### <a name="implicit-and-explicit-validation"></a>隱含和明確驗證  
 那麼, 控制項的資料何時會通過驗證？ 這是由開發人員所負責。 視應用程式的需求而定, 您可以使用隱含或明確驗證。  
  
#### <a name="implicit-validation"></a>隱含驗證  
 隱含驗證方法會在使用者輸入資料時進行驗證。 您可以在控制項中輸入資料時進行驗證, 方法是讀取按下的按鍵, 或在使用者將輸入焦點放在某個控制項時, 更頻繁地進行, 並移至下一個控制項。 當您想要讓使用者在資料正常運作時立即提供相關意見反應時, 這個方法很有用。  
  
 如果您想要對控制項使用隱含驗證, 則必須將該控制項的<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>屬性設為。 `true` 如果您取消<xref:System.Windows.Forms.Control.Validating>事件, 控制項的行為將取決於您<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>指派給的值。 如果您已<xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange>指派, 取消事件將<xref:System.Windows.Forms.Control.Validated>導致事件不會發生。 輸入焦點會保留在目前的控制項上, 直到使用者將資料變更為有效的輸入為止。 如果您指派<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>了, <xref:System.Windows.Forms.Control.Validated>當您取消事件時就不會發生此事件, 但焦點仍然會變更為下一個控制項。  
  
 <xref:System.Windows.Forms.AutoValidate.Disable> 指派<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>給屬性可防止全部隱含驗證。 若要驗證您的控制項, 您必須使用明確驗證。  
  
#### <a name="explicit-validation"></a>明確驗證  
 明確驗證方法會一次驗證資料。 您可以驗證資料以回應使用者動作, 例如按一下 [儲存] 按鈕或 [下一步] 連結。 當使用者動作發生時, 您可以透過下列其中一種方式來觸發明確驗證:  
  
- 呼叫<xref:System.Windows.Forms.ContainerControl.Validate%2A>以驗證最後一個控制項已失去焦點。  
  
- 呼叫<xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A>來驗證表單或容器控制項中的所有子控制項。  
  
- 呼叫自訂方法以手動驗證控制項中的資料。  
  
#### <a name="default-implicit-validation-behavior-for-windows-forms-controls"></a>Windows Forms 控制項的預設隱含驗證行為  
 不同的 Windows Forms 控制項的<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>屬性有不同的預設值。 下表顯示最常見的控制項及其預設值。  
  
|控制項|預設驗證行為|  
|-------------|---------------------------------|  
|<xref:System.Windows.Forms.ContainerControl>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
|<xref:System.Windows.Forms.PropertyGrid>|屬性未在 Visual Studio 中公開|  
|<xref:System.Windows.Forms.ToolStripContainer>|屬性未在 Visual Studio 中公開|  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
  
## <a name="closing-the-form-and-overriding-validation"></a>關閉表單並覆寫驗證  
 當控制項維護焦點時, 因為它所包含的資料無效, 所以無法以平常的其中一種方式關閉父表單:  
  
- 按一下 [**關閉**] 按鈕。  
  
- 在 [**系統**] 功能表中選取 [**關閉**]。  
  
- 以程式設計<xref:System.Windows.Forms.Form.Close%2A>方式呼叫方法。  
  
 不過, 在某些情況下, 您可能會想要讓使用者關閉表單, 而不論控制項中的值是否有效。 您可以藉由建立表單<xref:System.Windows.Forms.Form.Closing>事件的處理常式, 覆寫驗證, 並關閉仍然包含無效資料的表單。 在事件中, 將<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>屬性設定為。 `false` 這會強制關閉表單。 如需詳細資訊和範例，請參閱 <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>。  
  
> [!NOTE]
> 如果您強制表單以這種方式關閉, 表單控制項中尚未儲存的任何資料都會遺失。 此外, 強制回應表單在關閉時, 不會驗證控制項的內容。 您仍然可以使用控制項驗證來鎖定控制項的焦點, 但不需要擔心與關閉表單相關聯的行為。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Control.Validating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>
- <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType>
- [MaskedTextBox 控制項](./controls/maskedtextbox-control-windows-forms.md)
- [規則運算式範例](../../standard/base-types/regular-expression-examples.md)
