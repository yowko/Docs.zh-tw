---
title: PrintDocument 元件概觀
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: a82cc0cdcb8cfae796c9c6bf60ab73873f85a291
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728536"
---
# <a name="printdocument-component-overview-windows-forms"></a>PrintDocument 元件概觀 (Windows Form)

Windows Forms [PrintDocument](printdocument-component-windows-forms.md) 元件可用來設定描述列印項目的屬性，以及在 Windows 應用程式中列印文件的能力。 它可以與 [PrintDialog](printdialog-component-windows-forms.md) 元件一起使用，以控制文件列印的各個方面。

## <a name="working-with-the-printdocument-component"></a>使用 PrintDocument 元件

牽涉到 <xref:System.Drawing.Printing.PrintDocument> 元件的兩個主要案例如下：

- 簡單列印工作，例如列印個別的文字檔。 在這種情況下，您會將 <xref:System.Drawing.Printing.PrintDocument> 元件新增至 Windows Form，然後加入在 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件處理常式中列印檔案的程式設計邏輯。 程式設計邏輯應該使用 <xref:System.Drawing.Printing.PrintDocument.Print%2A> 方法來終於獲得，以列印檔案。 這個方法會將 <xref:System.Drawing.Printing.PrintPageEventArgs> 類別的 <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> 屬性中包含的 <xref:System.Drawing.Graphics> 物件傳送至印表機。 如需顯示如何使用 <xref:System.Drawing.Printing.PrintDocument> 元件來列印文字檔的範例，請參閱[如何：在 Windows Forms 中列印多頁文字檔](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)。

- 更複雜的列印工作，例如，您想要重複使用您所撰寫之列印邏輯的情況。 在這種情況下，您會從 <xref:System.Drawing.Printing.PrintDocument> 元件衍生新的元件，並覆寫（請參閱[Visual Basic](../../../csharp/language-reference/keywords/override.md)的C#[覆](../../../visual-basic/language-reference/modifiers/overrides.md)寫） <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件。

當它新增至表單時，<xref:System.Drawing.Printing.PrintDocument> 元件會出現在 Visual Studio Windows Form 設計工具底部的紙匣中。

## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [Windows Forms 列印支援](../advanced/windows-forms-print-support.md)
- [PrintDocument 元件](printdocument-component-windows-forms.md)
