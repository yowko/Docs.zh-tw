---
title: "OpenFileDialog 元件概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d3e5dc6630d9bc7a2090a28daabbf08eeed59005
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="openfiledialog-component-overview-windows-forms"></a><span data-ttu-id="21e27-102">OpenFileDialog 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="21e27-102">OpenFileDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="21e27-103">Windows Form <xref:System.Windows.Forms.OpenFileDialog> 元件是預先設定的對話方塊，</span><span class="sxs-lookup"><span data-stu-id="21e27-103">The Windows Forms <xref:System.Windows.Forms.OpenFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="21e27-104">它會是相同**開啟檔案**Windows 作業系統所公開的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="21e27-104">It is the same **Open File** dialog box exposed by the Windows operating system.</span></span> <span data-ttu-id="21e27-105">它繼承自 <xref:System.Windows.Forms.CommonDialog> 類別。</span><span class="sxs-lookup"><span data-stu-id="21e27-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="using-this-component"></a><span data-ttu-id="21e27-106">使用此元件</span><span class="sxs-lookup"><span data-stu-id="21e27-106">Using this Component</span></span>  
 <span data-ttu-id="21e27-107">作為此元件在 Windows 架構應用程式內的簡單解決方案就不需設定您自己的對話方塊中的檔案選取。</span><span class="sxs-lookup"><span data-stu-id="21e27-107">Use this component within your Windows-based application as a simple solution for file selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="21e27-108">藉由標準 Windows 對話方塊，建立使用者可立即熟悉基本功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="21e27-108">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="21e27-109">不過，要注意，當使用<xref:System.Windows.Forms.OpenFileDialog>元件，您必須撰寫您自己的檔案開啟邏輯。</span><span class="sxs-lookup"><span data-stu-id="21e27-109">Be aware, however, that when using the <xref:System.Windows.Forms.OpenFileDialog> component, you must write your own file-opening logic.</span></span>  
  
 <span data-ttu-id="21e27-110">使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法，以在執行階段顯示對話方塊。</span><span class="sxs-lookup"><span data-stu-id="21e27-110">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="21e27-111">您可以讓使用者多重選取的檔案，以使用開啟<xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="21e27-111">You can enable users to multi-select files to be opened with the <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> property.</span></span> <span data-ttu-id="21e27-112">此外，您可以使用<xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A>屬性來判斷是否唯讀核取方塊會出現在對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="21e27-112">Additionally, you can use the <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> property to determine if a read-only check box appears in the dialog box.</span></span> <span data-ttu-id="21e27-113"><xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A>屬性會指出是否選取唯讀核取方塊。</span><span class="sxs-lookup"><span data-stu-id="21e27-113">The <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> property indicates whether the read-only check box is selected.</span></span> <span data-ttu-id="21e27-114">最後，<xref:System.Windows.Forms.FileDialog.Filter%2A>屬性會設定目前檔案名稱篩選字串，以決定出現在 [檔案類型] 方塊中，在對話方塊中的選擇。</span><span class="sxs-lookup"><span data-stu-id="21e27-114">Finally, the <xref:System.Windows.Forms.FileDialog.Filter%2A> property sets the current file name filter string, which determines the choices that appear in the "Files of type" box in the dialog box.</span></span>  
  
 <span data-ttu-id="21e27-115">當加入至表單，<xref:System.Windows.Forms.OpenFileDialog>元件會出現在 Windows Form 設計工具底部的紙匣。</span><span class="sxs-lookup"><span data-stu-id="21e27-115">When it is added to a form, the <xref:System.Windows.Forms.OpenFileDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e27-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="21e27-116">See Also</span></span>  
 <xref:System.Windows.Forms.OpenFileDialog>  
 [<span data-ttu-id="21e27-117">OpenFileDialog 元件</span><span class="sxs-lookup"><span data-stu-id="21e27-117">OpenFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
