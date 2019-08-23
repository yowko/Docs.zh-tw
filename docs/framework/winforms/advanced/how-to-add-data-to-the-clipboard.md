---
title: 作法：將資料新增至剪貼簿
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- data [Windows Forms], copying to Clipboard
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
ms.openlocfilehash: d4afcd6ce942d1cd2286e3f393ce61436821bb3a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955118"
---
# <a name="how-to-add-data-to-the-clipboard"></a>HOW TO：將資料新增至剪貼簿
<xref:System.Windows.Forms.Clipboard>類別提供的方法可讓您用來與 Windows 作業系統剪貼簿功能進行互動。 許多應用程式會使用剪貼簿做為資料的暫存存放庫。 例如, 字處理器會在剪下和貼上作業期間使用剪貼簿。 剪貼簿也適用于將資料從一個應用程式傳送到另一個。  
  
 當您將資料新增至剪貼簿時, 您可以指定資料格式, 讓其他應用程式可以使用該格式來辨識資料。 您也可以使用多種不同的格式將資料新增至剪貼簿, 以增加可能使用該資料的其他應用程式數目。  
  
 剪貼簿格式是識別格式的字串, 因此使用該格式的應用程式可以抓取相關聯的資料。 <xref:System.Windows.Forms.DataFormats>類別會為您的用途提供預先定義的格式名稱。 您也可以使用自己的格式名稱, 或使用物件的類型做為其格式。  
  
 若要以一或多個格式將資料新增至剪貼簿<xref:System.Windows.Forms.Clipboard.SetDataObject%2A> , 請使用方法。 您可以將任何物件傳遞至此方法, 但是若要以多種格式加入資料, 您必須先將資料新增至專為使用多種格式而設計的個別物件。 一般來說, 您會將資料加入至<xref:System.Windows.Forms.DataObject>, 但是您可以使用任何可實作為<xref:System.Windows.Forms.IDataObject>介面的型別。  
  
 在 .NET Framework 2.0 中, 您可以使用新的方法, 將資料直接加入剪貼簿, 使基本剪貼簿工作更容易。 當您以單一通用格式 (例如文字) 處理資料時, 請使用這些方法。  
  
> [!NOTE]
> 所有 Windows 應用程式都會共用剪貼簿。 因此, 當您切換到另一個應用程式時, 內容可能會變更。  
>   
>  <xref:System.Windows.Forms.Clipboard>類別只能用在設定為單一執行緒單元 (STA) 模式的執行緒中。 若要使用這個類別, 請確定`Main`您的方法是<xref:System.STAThreadAttribute>以屬性標記。  
>   
>  物件必須是可序列化的, 才能放在剪貼簿上。 若要讓類型成為可序列化, 請將<xref:System.SerializableAttribute>它標記為屬性。 如果您將不可序列化的物件傳遞至剪貼簿方法, 此方法將會失敗, 而不會擲回例外狀況。 如需序列化的詳細資訊，請參閱 <xref:System.Runtime.Serialization>。  
  
### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a>以單一通用格式將資料新增至剪貼簿  
  
1. <xref:System.Windows.Forms.Clipboard.SetAudio%2A>使用、<xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>、或<xref:System.Windows.Forms.Clipboard.SetText%2A>方法。 <xref:System.Windows.Forms.Clipboard.SetImage%2A> 這些方法僅適用于 .NET Framework 2.0。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a>以自訂格式將資料新增至剪貼簿  
  
1. 使用具有<xref:System.Windows.Forms.Clipboard.SetData%2A>自訂格式名稱的方法。 這個方法僅適用于 .NET Framework 2.0。  
  
     您也可以搭配<xref:System.Windows.Forms.Clipboard.SetData%2A>方法使用預先定義的格式名稱。 如需詳細資訊，請參閱 <xref:System.Windows.Forms.DataFormats>。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a>以多種格式將資料新增至剪貼簿  
  
1. 使用方法, 並傳入<xref:System.Windows.Forms.DataObject>包含您資料的。 <xref:System.Windows.Forms.Clipboard.SetDataObject%2A?displayProperty=nameWithType> 您必須使用這個方法, 在 .NET Framework 2.0 之前的版本上, 將資料新增至剪貼簿。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>另請參閱

- [拖放作業和剪貼簿支援](drag-and-drop-operations-and-clipboard-support.md)
- [如何：從剪貼簿取出資料](how-to-retrieve-data-from-the-clipboard.md)
