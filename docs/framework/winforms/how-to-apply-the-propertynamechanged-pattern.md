---
title: HOW TO：套用 PropertyNameChanged 模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- data binding [Windows Forms], custom controls
- PropertyNameChanged pattern [Windows Forms], applying
ms.assetid: aa47ddf6-5223-40c4-833f-a78992194836
ms.openlocfilehash: 36670eee6235277a7fe98770192df9ae05d3dd03
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966812"
---
# <a name="how-to-apply-the-propertynamechanged-pattern"></a>HOW TO：套用 PropertyNameChanged 模式
下列程式碼範例示範如何套用*PropertyName*自訂控制項模式。 當您實作自訂控制項，可搭配 Windows Form 資料繫結引擎，適用於這種模式。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要編譯上述程式碼範例：  
  
- 程式碼貼到空白程式碼檔案。 您必須使用自訂控制項，其中包含 Windows Form 上的`Main`方法。  
  
## <a name="see-also"></a>另請參閱

- [如何：實作 INotifyPropertyChanged 介面](how-to-implement-the-inotifypropertychanged-interface.md)
- [Windows Forms 資料繫結中的變更告知](change-notification-in-windows-forms-data-binding.md)
- [Windows Forms 資料繫結](windows-forms-data-binding.md)
