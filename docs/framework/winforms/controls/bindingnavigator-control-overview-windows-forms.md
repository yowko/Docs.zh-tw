---
title: BindingNavigator 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- DataNavigator
helpviewer_keywords:
- BindingNavigator control [Windows Forms], about BindingNavigator control
- records [Windows Forms], navigating on a form
- data [Windows Forms], navigating
- data navigation
ms.assetid: 4423eede-f8d1-4d02-822f-5bf8432680d0
ms.openlocfilehash: 06ad69b7ad40e85dfbb18a170e0a72095e711b83
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54533110"
---
# <a name="bindingnavigator-control-overview-windows-forms"></a>BindingNavigator 控制項概觀 (Windows Form)
您可以使用 <xref:System.Windows.Forms.BindingNavigator> 控制項來建立標準化的方法，讓使用者用來搜尋和變更 Windows Form 上的資料。 您經常使用 <xref:System.Windows.Forms.BindingNavigator> 搭配 <xref:System.Windows.Forms.BindingSource> 元件，讓使用者能夠瀏覽表單上的資料記錄，以及與記錄互動。  
  
## <a name="how-the-bindingnavigator-works"></a>BindingNavigator 的運作方式  
 <xref:System.Windows.Forms.BindingNavigator> 控制項是由 <xref:System.Windows.Forms.ToolStrip> 與一系列 <xref:System.Windows.Forms.ToolStripItem> 物件所組成，可用來進行大多數常見的資料相關動作：加入資料、刪除資料，以及巡覽資料。 根據預設，<xref:System.Windows.Forms.BindingNavigator> 控制項會包含這些標準按鈕。 下列螢幕擷取畫面顯示表單上的 <xref:System.Windows.Forms.BindingNavigator> 控制項。  
  
 ![BindingNavigator Control](../../../../docs/framework/winforms/controls/media/cpdatacontainerctrl.gif "cpDataContainerCtrl")  
  
 下表列出控制項，並描述其功能。  
  
|控制項|函式|  
|-------------|--------------|  
|<xref:System.Windows.Forms.BindingNavigator.AddNewItem%2A> 按鈕|將新資料列插入基礎資料來源中。|  
|<xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> 按鈕|從基礎資料來源中刪除目前的資料列。|  
|<xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> 按鈕|移至基礎資料來源中的第一個項目。|  
|<xref:System.Windows.Forms.BindingNavigator.MoveLastItem%2A> 按鈕|移至基礎資料來源中的最後一個項目。|  
|<xref:System.Windows.Forms.BindingNavigator.MoveNextItem%2A> 按鈕|移至基礎資料來源中的下一個項目。|  
|<xref:System.Windows.Forms.BindingNavigator.MovePreviousItem%2A> 按鈕|移至基礎資料來源中的上一個項目。|  
|<xref:System.Windows.Forms.BindingNavigator.PositionItem%2A> 文字方塊|傳回在基礎資料來源內的目前位置。|  
|<xref:System.Windows.Forms.BindingNavigator.CountItem%2A> 文字方塊|傳回基礎資料來源中的項目總數。|  
  
 針對此集合中的每個控制項，各有一個 <xref:System.Windows.Forms.BindingSource> 元件的對應成員，它會以程式設計的方式提供相同的功能。 例如，<xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> 按鈕對應至 <xref:System.Windows.Forms.BindingSource> 元件的 <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> 方法，<xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> 按鈕對應至 <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> 方法等。  
  
 如果預設按鈕不適合您的應用程式，或者如果您需要其他按鈕來支援其他類型的功能，您可以提供自己的 <xref:System.Windows.Forms.ToolStrip> 按鈕。 另請參閱[How to:將載入、 儲存，和 [取消] 按鈕，以 Windows Forms BindingNavigator 控制項](../../../../docs/framework/winforms/controls/load-save-and-cancel-bindingnavigator.md)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- [BindingNavigator 控制項](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)
