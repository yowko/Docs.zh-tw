---
title: 如何：套用 PropertyNameChanged 模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- data binding [Windows Forms], custom controls
- PropertyNameChanged pattern [Windows Forms], applying
ms.assetid: aa47ddf6-5223-40c4-833f-a78992194836
ms.openlocfilehash: 775a27b1b4ba8143e297a3c4d323356a304073a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536741"
---
# <a name="how-to-apply-the-propertynamechanged-pattern"></a>如何：套用 PropertyNameChanged 模式
下列程式碼範例示範如何套用*PropertyName*模式設為自訂控制項。 當您實作自訂控制項搭配 Windows Form 資料繫結引擎所使用時，適用於此模式。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要編譯先前的程式碼範例：  
  
-   將程式碼貼到空白程式碼檔案。 您必須使用包含在 Windows Form 上的自訂控制項`Main`方法。  
  
## <a name="see-also"></a>另請參閱  
 [操作說明：實作 INotifyPropertyChanged 介面](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)  
 [Windows Forms 資料繫結中的變更告知](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [Windows Forms 資料繫結](../../../docs/framework/winforms/windows-forms-data-binding.md)
