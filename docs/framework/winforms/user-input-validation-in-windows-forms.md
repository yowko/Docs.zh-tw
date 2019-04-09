---
title: Windows Form 中的使用者輸入驗證
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, validating user input
- validation [Windows Forms], Windows Forms user input
- user input [Windows Forms], validating in Windows Forms
- validating user input [Windows Forms], Windows Forms
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
ms.openlocfilehash: c8a40706df4274728b438cff2539173a0e94b767
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076675"
---
# <a name="user-input-validation-in-windows-forms"></a>Windows Form 中的使用者輸入驗證
當使用者將資料輸入您的應用程式時，您可以確認資料有效，您的應用程式會使用它之前。 您可能需要某些文字欄位不是零長度、 欄位會格式化為電話號碼或其他類型的格式正確的資料，或字串不包含任何不安全的字元可以用來危害的資料庫安全性。 Windows Form 提供幾種方式可以驗證您的應用程式中的輸入。  
  
## <a name="validation-with-the-maskedtextbox-control"></a>驗證與 MaskedTextBox 控制項  
 若要要求使用者輸入資料中定義完善的格式，例如電話號碼或零件編號，您可以達成快速且最少程式碼使用<xref:System.Windows.Forms.MaskedTextBox>控制項。 A*遮罩*是從指定的字元可以在任何給定的位置，在文字方塊中輸入的遮罩語言的字元所組成的字串。 控制向使用者顯示一組提示。 如果使用者輸入不正確的項目，例如，使用者輸入的字母，需要數字時，控制項將會自動拒絕輸入。  
  
 所使用的遮罩語言<xref:System.Windows.Forms.MaskedTextBox>極具彈性。 它可讓您指定必要的字元、 選擇性字元、 常值字元，例如連字號和括號、 貨幣字元和日期分隔符號。 控制項也適用於也當繫結至資料來源。 <xref:System.Windows.Forms.Binding.Format>事件的資料繫結可用來將內送的資料，以符合與遮罩，重新格式化和<xref:System.Windows.Forms.Binding.Parse>事件可用來重新格式化傳出的資料，以符合與資料欄位的規格。  
  
 如需詳細資訊，請參閱 < [MaskedTextBox 控制項](./controls/maskedtextbox-control-windows-forms.md)。  
  
## <a name="event-driven-validation"></a>事件導向的驗證  
 如果您想要完整的程式設計控制驗證，或需要來執行複雜的驗證檢查，您應該使用內建大部分的 Windows Form 控制項的驗證事件。 每個控制項可接受自由格式的使用者輸入具有<xref:System.Windows.Forms.Control.Validating>每當控制項需要資料驗證會發生的事件。 在 <xref:System.Windows.Forms.Control.Validating>事件處理方法，您可以驗證使用者輸入以數種方式。 比方說，如果您有必須包含郵遞區號文字方塊中，您可以透過下列方式來執行驗證：  
  
-   如果郵遞區號必須屬於特定群組的郵遞區號，您可以執行字串比較，來驗證使用者輸入的資料輸入。 比方說，如果郵遞區號必須是集中 {10001、 10002，10003}，然後您可以使用字串比較的資料進行驗證。  
  
-   如果郵遞區號必須位於特定的表單，您可以使用規則運算式來驗證使用者輸入的資料。 例如，若要驗證的表單`#####`或是`#####-####`，您可以使用規則運算式`^(\d{5})(-\d{4})?$`。 若要驗證的表單`A#A #A#`，您可以使用規則運算式`[A-Z]\d[A-Z] \d[A-Z]\d`。 如需有關規則運算式的詳細資訊，請參閱 < [.NET Framework 規則運算式](../../standard/base-types/regular-expressions.md)並[規則運算式範例](../../standard/base-types/regular-expression-examples.md)。  
  
-   如果郵遞區號必須是有效的美國郵遞區號，您可以呼叫郵遞區號 Web 服務，以驗證使用者輸入的資料。  
  
 <xref:System.Windows.Forms.Control.Validating>事件會提供型別的物件<xref:System.ComponentModel.CancelEventArgs>。 如果您判斷控制項的資料無效，您可以取消<xref:System.Windows.Forms.Control.Validating>藉由設定這個物件的事件<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>屬性設`true`。 如果您未設定<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>屬性，Windows Forms 會假設該控制項中，已成功驗證並引發<xref:System.Windows.Forms.Control.Validated>事件。  
  
 程式碼範例會驗證電子郵件地址<xref:System.Windows.Controls.TextBox>，請參閱<xref:System.Windows.Forms.Control.Validating>。  
  
### <a name="data-binding-and-event-driven-validation"></a>資料繫結和事件導向的驗證  
 當您已將您的控制項繫結至資料來源，例如資料庫資料表時，驗證將會非常有用。 使用驗證，您可以確保控制項的資料符合資料來源，所需的格式，和，它不包含任何特殊字元，例如引號，然後傳回斜線，可能不安全。  
  
 當您使用資料繫結時，您的控制項中的資料會同步處理與資料來源執行期間<xref:System.Windows.Forms.Control.Validating>事件。 如果您取消<xref:System.Windows.Forms.Control.Validating>事件，資料將不會與資料來源同步。  
  
> [!IMPORTANT]
>  如果您有自訂的驗證，之後會進行<xref:System.Windows.Forms.Control.Validating>事件，它不會影響資料繫結。 例如，如果您在程式碼<xref:System.Windows.Forms.Control.Validated>嘗試取消資料繫結的事件，資料繫結仍會發生。 在此情況下，執行中的驗證<xref:System.Windows.Forms.Control.Validated>事件，變更控制項的**資料來源更新模式**屬性 (**在 (Databindings) 下**\\ **（進階）**) 從**OnValidation**要**永不**，並新增*控制*`.DataBindings["`*\<YOURFIELD >* `"].WriteValue()`來驗證程式碼。  
  
### <a name="implicit-and-explicit-validation"></a>隱含和明確的驗證  
 所以當沒有控制項的資料驗證？ 這是由您，開發人員決定。 您可以使用隱含或明確的驗證，根據您的應用程式的需求。  
  
#### <a name="implicit-validation"></a>隱含驗證  
 隱含的驗證方法驗證資料，當使用者輸入它。 在使用者按下，讀取金鑰的控制項或多個輸入資料，時使用者會將輸入的焦點從一個控制項，並將移至下一步 時，通常，您可以驗證資料。 當您想要提供有關資料的使用者立即回應，就在工作時，這個方法很有用。  
  
 如果您想要使用控制項的隱含驗證，您必須設定該控制項<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>屬性設`true`。 如果您取消<xref:System.Windows.Forms.Control.Validating>事件，控制項的行為取決於何值，您指派給<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>。 如果您指派<xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange>，取消事件將會讓<xref:System.Windows.Forms.Control.Validated>不發生的事件。 輸入的焦點將仍保留在目前的控制項，直到使用者將變更為有效的輸入資料。 如果您指派<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>，則<xref:System.Windows.Forms.Control.Validated>取消事件，但焦點還是會變更至下一個控制項時，不會發生事件。  
  
 指派<xref:System.Windows.Forms.AutoValidate.Disable>至<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>屬性完全防止隱含的驗證。 若要驗證您的控制項，您必須使用明確的驗證。  
  
#### <a name="explicit-validation"></a>明確的驗證  
 明確的驗證方法驗證其資料一次。 您可以驗證使用者的動作，例如按一下 儲存 按鈕或下一步 連結的回應中的資料。 使用者動作時，您可以透過下列方式之一來觸發明確驗證：  
  
-   呼叫<xref:System.Windows.Forms.ContainerControl.Validate%2A>驗證的最後一個控制項失去焦點。  
  
-   呼叫<xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A>驗證表單或容器控制項中的所有子控制項。  
  
-   呼叫自訂的方法，以手動方式驗證控制項中的資料。  
  
#### <a name="default-implicit-validation-behavior-for-windows-forms-controls"></a>預設隱含的驗證行為，如 Windows Forms 控制項  
 不同的 Windows Form 控制項有不同的預設值為其<xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>屬性。 下表顯示最常見的控制項和其預設值。  
  
|控制項|預設驗證行為|  
|-------------|---------------------------------|  
|<xref:System.Windows.Forms.ContainerControl>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
|<xref:System.Windows.Forms.PropertyGrid>|Visual Studio 中未公開的屬性|  
|<xref:System.Windows.Forms.ToolStripContainer>|Visual Studio 中未公開的屬性|  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
  
## <a name="closing-the-form-and-overriding-validation"></a>關閉表單並覆寫驗證  
 當控制項維護焦點，因為它所包含的資料無效時，就無法關閉父表單，其中一種一般的方式：  
  
-   依序按一下**關閉** 按鈕。  
  
-   藉由選取**關閉**中**系統**功能表。  
  
-   藉由呼叫<xref:System.Windows.Forms.Form.Close%2A>方法以程式設計的方式。  
  
 不過，在某些情況下，您可能想要讓使用者關閉表單，不論控制項中的值是否有效。 您可以覆寫驗證並關閉仍包含無效的資料，藉由建立表單的處理常式的表單<xref:System.Windows.Forms.Form.Closing>事件。 在事件中，設定<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>屬性設`false`。 這會強制關閉表單。 如需詳細資訊和範例，請參閱 <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>。  
  
> [!NOTE]
>  如果您強制以這種方式關閉表單，表單控制項中且已儲存的任何資料將會遺失。 此外，強制回應表單不會驗證控制項的內容，在關閉時。 您仍然可以使用控制驗證鎖定至控制項時，焦點，但您不一定要擔心與關閉表單相關聯的行為。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Control.Validating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>
- <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType>
- [MaskedTextBox 控制項](./controls/maskedtextbox-control-windows-forms.md)
- [規則運算式範例](../../standard/base-types/regular-expression-examples.md)
