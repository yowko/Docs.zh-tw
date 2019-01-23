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
ms.openlocfilehash: 82856405ab3c9581b398f358e5bf9ecf989ce193
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539762"
---
# <a name="how-to-apply-the-propertynamechanged-pattern"></a><span data-ttu-id="78126-102">HOW TO：套用 PropertyNameChanged 模式</span><span class="sxs-lookup"><span data-stu-id="78126-102">How to: Apply the PropertyNameChanged Pattern</span></span>
<span data-ttu-id="78126-103">下列程式碼範例示範如何套用*PropertyName*自訂控制項模式。</span><span class="sxs-lookup"><span data-stu-id="78126-103">The following code example demonstrates how to apply the *PropertyName*Changed pattern to a custom control.</span></span> <span data-ttu-id="78126-104">當您實作自訂控制項，可搭配 Windows Form 資料繫結引擎，適用於這種模式。</span><span class="sxs-lookup"><span data-stu-id="78126-104">Apply this pattern when you implement custom controls that are used with the Windows Forms data binding engine.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78126-105">範例</span><span class="sxs-lookup"><span data-stu-id="78126-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="78126-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="78126-106">Compiling the Code</span></span>  
 <span data-ttu-id="78126-107">若要編譯上述程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="78126-107">To compile the previous code example:</span></span>  
  
-   <span data-ttu-id="78126-108">程式碼貼到空白程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="78126-108">Paste the code into an empty code file.</span></span> <span data-ttu-id="78126-109">您必須使用自訂控制項，其中包含 Windows Form 上的`Main`方法。</span><span class="sxs-lookup"><span data-stu-id="78126-109">You must use the custom control on a Windows Form that contains a `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78126-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78126-110">See also</span></span>
- [<span data-ttu-id="78126-111">如何：實作 INotifyPropertyChanged 介面</span><span class="sxs-lookup"><span data-stu-id="78126-111">How to: Implement the INotifyPropertyChanged Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)
- [<span data-ttu-id="78126-112">Windows Forms 資料繫結中的變更告知</span><span class="sxs-lookup"><span data-stu-id="78126-112">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)
- [<span data-ttu-id="78126-113">Windows Forms 資料繫結</span><span class="sxs-lookup"><span data-stu-id="78126-113">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
