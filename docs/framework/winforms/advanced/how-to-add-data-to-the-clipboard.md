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
ms.openlocfilehash: 06ce64de5e2a6b4aa299b9ad9c41982b7c1924c7
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348269"
---
# <a name="how-to-add-data-to-the-clipboard"></a>作法：將資料新增至剪貼簿
<xref:System.Windows.Forms.Clipboard>類別提供方法，您可以使用與 Windows 作業系統的剪貼簿功能互動。 許多應用程式資料做為暫存的儲存機制使用剪貼簿。 例如，文書處理器使用剪貼簿剪下和貼上作業期間。 也適用於將資料傳輸到另一個應用程式從剪貼簿。  
  
 當您新增到剪貼簿的資料時，您可以指定資料格式，使其他應用程式可以辨識的資料，是否能夠使用該格式。 您也可以將資料加入多個不同的格式剪貼簿，增加的數目可能可以使用這些資料的其他應用程式中。  
  
 剪貼簿格式為字串，識別格式，以便使用該格式的應用程式可以擷取相關聯的資料。 <xref:System.Windows.Forms.DataFormats>類別會提供給您使用的預先定義的格式名稱。 您也可以使用您自己的格式名稱，或物件類型做為它的格式。  
  
 若要將資料加入至一個或多個格式剪貼簿 中，使用<xref:System.Windows.Forms.Clipboard.SetDataObject%2A>方法。 您可以將任何物件傳遞至這個方法，但若要新增以多種格式的資料，您必須先將資料加入設計用於搭配多種格式的個別物件。 一般而言，您將在其中加入您的資料<xref:System.Windows.Forms.DataObject>，但您可以使用任何可實作型別<xref:System.Windows.Forms.IDataObject>介面。  
  
 在.NET Framework 2.0 中，您可以將資料直接加入剪貼簿使用旨在讓您更輕鬆的剪貼簿的基本工作的新方法。 當您使用單一、 通用的格式，例如文字的資料時，請使用這些方法。  
  
> [!NOTE]
>  所有以 Windows 為基礎的應用程式共用剪貼簿。 因此，內容會有所變更中是當您切換到另一個應用程式。  
>   
>  <xref:System.Windows.Forms.Clipboard>類別只能設定為單一執行緒 apartment (STA) 模式的執行緒中。 若要使用這個類別，請確認您`Main`方法會標示<xref:System.STAThreadAttribute>屬性。  
>   
>  物件必須可序列化，才能放在剪貼簿。 若要讓可序列化的型別，加以標示<xref:System.SerializableAttribute>屬性。 如果您將不可序列化物件傳遞至剪貼簿方法時，此方法將會失敗而不擲回例外狀況。 如需序列化的詳細資訊，請參閱 <xref:System.Runtime.Serialization>。  
  
### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a>若要將資料加入至單一的常用格式剪貼簿  
  
1. 使用<xref:System.Windows.Forms.Clipboard.SetAudio%2A>， <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>， <xref:System.Windows.Forms.Clipboard.SetImage%2A>，或<xref:System.Windows.Forms.Clipboard.SetText%2A>方法。 這些方法是僅適用於.NET Framework 2.0。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a>若要將資料加入至剪貼簿中的自訂格式  
  
1. 使用<xref:System.Windows.Forms.Clipboard.SetData%2A>方法以自訂格式名稱。 這個方法是僅適用於.NET Framework 2.0。  
  
     您也可以使用預先定義的格式名稱<xref:System.Windows.Forms.Clipboard.SetData%2A>方法。 如需詳細資訊，請參閱 <xref:System.Windows.Forms.DataFormats>。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a>若要將資料加入至剪貼簿以多種格式  
  
1. 使用<xref:System.Windows.Forms.Clipboard.SetDataObject%2A?displayProperty=nameWithType>方法並傳入<xref:System.Windows.Forms.DataObject>其中包含您的資料。 您必須使用這個方法將資料加入至版本早於.NET Framework 2.0 的剪貼簿。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>另請參閱

- [拖放作業和剪貼簿支援](drag-and-drop-operations-and-clipboard-support.md)
- [如何：從剪貼簿擷取資料](how-to-retrieve-data-from-the-clipboard.md)
