---
title: ErrorProvider 元件概觀
ms.date: 03/30/2017
f1_keywords:
- ErrorProvider
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error messages [Windows Forms], displaying
- ErrorProvider component [Windows Forms], about ErrorProvider component
ms.assetid: ced189f2-b5c8-46a7-a6f1-37f5af95dc99
ms.openlocfilehash: b66e97d97d0d8c2ea4e9bdba29f8ff35e486e1f6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745799"
---
# <a name="errorprovider-component-overview-windows-forms"></a>ErrorProvider 元件概觀 (Windows Form)
Windows Forms [ErrorProvider](errorprovider-component-windows-forms.md)元件是用來驗證表單或控制項上的使用者輸入。 它通常會與驗證表單上的使用者輸入，或在資料集內顯示錯誤一起使用。 錯誤提供者是比在訊息方塊中顯示錯誤訊息更好的替代方式，因為一旦關閉訊息方塊，就不會再看到錯誤訊息。 <xref:System.Windows.Forms.ErrorProvider> 元件會在相關控制項（例如文字方塊）旁顯示錯誤圖示（![紅色圓形內的白色驚嘆號）](./media/errorprovider-component-overview-windows-forms/vb-error-provider-icon.gif)。當使用者將滑鼠指標放在錯誤圖示上方時，會出現工具提示，顯示錯誤訊息字串。  
  
## <a name="key-properties"></a>索引鍵內容  
 <xref:System.Windows.Forms.ErrorProvider> 元件的索引鍵屬性是 <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>、<xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>和 <xref:System.Windows.Forms.ErrorProvider.Icon%2A>。 搭配使用 <xref:System.Windows.Forms.ErrorProvider> 元件與資料繫結控制項時，<xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> 屬性必須設定為適當的容器（通常是 Windows Form），元件才會在表單上顯示錯誤圖示。 當元件新增至設計工具時，<xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> 屬性會設定為包含表單;如果您在程式碼中加入控制項，則必須自行設定。  
  
 <xref:System.Windows.Forms.ErrorProvider.Icon%2A> 屬性可以設定為自訂錯誤圖示，而不是預設值。 設定 [<xref:System.Windows.Forms.ErrorProvider.DataSource%2A>] 屬性時，<xref:System.Windows.Forms.ErrorProvider> 元件可以顯示資料集的錯誤訊息。 <xref:System.Windows.Forms.ErrorProvider> 元件的主要方法是 <xref:System.Windows.Forms.ErrorProvider.SetError%2A> 方法，它會指定錯誤訊息字串，以及應該出現錯誤圖示的位置。  
  
> [!NOTE]
> <xref:System.Windows.Forms.ErrorProvider> 元件並未提供協助工具用戶端的內建支援。 若要讓您的應用程式在使用此元件時可供存取，您必須提供其他可存取的意見反應機制。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.ErrorProvider>
- [操作說明：使用 Windows Forms ErrorProvider 元件檢視資料集錯誤](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
- [操作說明：使用 Windows Forms ErrorProvider 元件顯示表單驗證的錯誤圖示](display-error-icons-for-form-validation-with-wf-errorprovider.md)
