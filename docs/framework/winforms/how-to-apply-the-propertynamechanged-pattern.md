---
title: "如何：套用 PropertyNameChanged 模式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- data binding [Windows Forms], custom controls
- PropertyNameChanged pattern [Windows Forms], applying
ms.assetid: aa47ddf6-5223-40c4-833f-a78992194836
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1afe397a92ac6e79e84757baa0c41f6e0c54b7f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-the-propertynamechanged-pattern"></a><span data-ttu-id="27404-102">如何：套用 PropertyNameChanged 模式</span><span class="sxs-lookup"><span data-stu-id="27404-102">How to: Apply the PropertyNameChanged Pattern</span></span>
<span data-ttu-id="27404-103">下列程式碼範例示範如何套用*PropertyName*模式設為自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="27404-103">The following code example demonstrates how to apply the *PropertyName*Changed pattern to a custom control.</span></span> <span data-ttu-id="27404-104">當您實作自訂控制項搭配 Windows Form 資料繫結引擎所使用時，適用於此模式。</span><span class="sxs-lookup"><span data-stu-id="27404-104">Apply this pattern when you implement custom controls that are used with the Windows Forms data binding engine.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27404-105">範例</span><span class="sxs-lookup"><span data-stu-id="27404-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="27404-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="27404-106">Compiling the Code</span></span>  
 <span data-ttu-id="27404-107">若要編譯先前的程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="27404-107">To compile the previous code example:</span></span>  
  
-   <span data-ttu-id="27404-108">將程式碼貼到空白程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="27404-108">Paste the code into an empty code file.</span></span> <span data-ttu-id="27404-109">您必須使用包含在 Windows Form 上的自訂控制項`Main`方法。</span><span class="sxs-lookup"><span data-stu-id="27404-109">You must use the custom control on a Windows Form that contains a `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27404-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="27404-110">See Also</span></span>  
 [<span data-ttu-id="27404-111">操作說明：實作 INotifyPropertyChanged 介面</span><span class="sxs-lookup"><span data-stu-id="27404-111">How to: Implement the INotifyPropertyChanged Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)  
 [<span data-ttu-id="27404-112">Windows Forms 資料繫結中的變更告知</span><span class="sxs-lookup"><span data-stu-id="27404-112">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [<span data-ttu-id="27404-113">Windows Forms 資料繫結</span><span class="sxs-lookup"><span data-stu-id="27404-113">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
