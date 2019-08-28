---
title: 作法：從剪貼簿擷取資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pasting Clipboard data
- Clipboard [Windows Forms], retrieving data
ms.assetid: 99612537-2c8a-449f-aab5-2b3b28d656e7
ms.openlocfilehash: ca24615049abcc145698c033f31e6c98a38253bf
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040573"
---
# <a name="how-to-retrieve-data-from-the-clipboard"></a>作法：從剪貼簿擷取資料

<xref:System.Windows.Forms.Clipboard>類別提供的方法可讓您用來與 Windows 作業系統剪貼簿功能進行互動。 許多應用程式會使用剪貼簿做為資料的暫存存放庫。 例如, 字處理器會在剪下和貼上作業期間使用剪貼簿。 剪貼簿也很適合用來將資訊從一個應用程式傳送到另一個。

有些應用程式會以多種格式將資料儲存在剪貼簿上, 以增加可能使用資料的其他應用程式數目。 剪貼簿格式是可識別格式的字串。 使用已識別格式的應用程式可以抓取剪貼簿上的相關資料。 <xref:System.Windows.Forms.DataFormats>類別會為您的用途提供預先定義的格式名稱。 您也可以使用自己的格式名稱, 或使用物件的類型做為其格式。 如需將資料新增至剪貼簿的相關[資訊, 請參閱如何:將資料新增至剪貼](how-to-add-data-to-the-clipboard.md)簿。

若要判斷剪貼簿是否包含特定格式的資料, 請使用其中一`Contains`種*格式*方法或<xref:System.Windows.Forms.Clipboard.GetData%2A>方法。 若要從剪貼簿取出資料, 請使用其中`Get`一種*格式*方法<xref:System.Windows.Forms.Clipboard.GetData%2A>或方法。 這些方法是 .NET Framework 2.0 中的新功能。

若要使用早于 .NET Framework 2.0 的版本來存取剪貼簿中的資料<xref:System.Windows.Forms.Clipboard.GetDataObject%2A?displayProperty=nameWithType> , 請使用方法, 並呼叫所<xref:System.Windows.Forms.IDataObject>傳回之的方法。 若要判斷傳回的物件中是否有特定的格式, 例如, 請呼叫<xref:System.Windows.Forms.IDataObject.GetDataPresent%2A>方法。

> [!NOTE]
> 所有 Windows 應用程式都會共用系統剪貼簿。 因此, 當您切換到另一個應用程式時, 內容可能會變更。
>
> <xref:System.Windows.Forms.Clipboard>類別只能用在設定為單一執行緒單元 (STA) 模式的執行緒中。 若要使用這個類別, 請確定`Main`您的方法是<xref:System.STAThreadAttribute>以屬性標記。

### <a name="to-retrieve-data-from-the-clipboard-in-a-single-common-format"></a>以單一通用格式從剪貼簿取出資料

1. <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>使用、<xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>、或<xref:System.Windows.Forms.Clipboard.GetText%2A>方法。 <xref:System.Windows.Forms.Clipboard.GetImage%2A> (選擇性) 先使用`Contains`對應的*格式*方法, 以判斷資料是否以特定格式提供。 這些方法僅適用于 .NET Framework 2.0。

    [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
    [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]

### <a name="to-retrieve-data-from-the-clipboard-in-a-custom-format"></a>以自訂格式從剪貼簿取出資料

1. 使用具有<xref:System.Windows.Forms.Clipboard.GetData%2A>自訂格式名稱的方法。 這個方法僅適用于 .NET Framework 2.0。

    您也可以搭配<xref:System.Windows.Forms.Clipboard.SetData%2A>方法使用預先定義的格式名稱。 如需詳細資訊，請參閱 <xref:System.Windows.Forms.DataFormats>。

    [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
    [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]

### <a name="to-retrieve-data-from-the-clipboard-in-multiple-formats"></a>以多種格式從剪貼簿取出資料

1. 請使用 <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> 方法。 您必須使用這個方法, 在早于 .NET Framework 2.0 的版本上, 從剪貼簿取出資料。

    [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
    [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]

## <a name="see-also"></a>另請參閱

- [拖放作業和剪貼簿支援](drag-and-drop-operations-and-clipboard-support.md)
- [如何：將資料新增至剪貼簿](how-to-add-data-to-the-clipboard.md)
