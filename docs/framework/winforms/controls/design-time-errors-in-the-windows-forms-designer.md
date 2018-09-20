---
title: Windows Form 設計工具的設計階段錯誤
ms.date: 03/30/2017
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
ms.openlocfilehash: ec1801a1b695867a7edcd99394feebe1d0f6853a
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "46490136"
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a><span data-ttu-id="2c400-102">Windows Form 設計工具的設計階段錯誤</span><span class="sxs-lookup"><span data-stu-id="2c400-102">Design-Time Errors in the Windows Forms Designer</span></span>
<span data-ttu-id="2c400-103">本主題說明當 Windows Forms 設計工具載入失敗時，Microsoft Visual Studio 中所出現的設計階段錯誤清單的意義與用法。</span><span class="sxs-lookup"><span data-stu-id="2c400-103">This topic explains the meaning and use of the design-time error list that appears in Microsoft Visual Studio when the Windows Forms Designer fails to load.</span></span> <span data-ttu-id="2c400-104">如果出現此錯誤清單，您不應該將它視為是設計工具中的錯誤，而是協助您更正程式碼中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="2c400-104">If this error list appears, you should not interpret it as a bug in the designer, but as an aid to correcting errors in your code.</span></span>  
  
 <span data-ttu-id="2c400-105">在基本上了解此錯誤清單會提供錯誤的詳細資訊並建議可能的解決方案，將有助於您偵錯應用程式。</span><span class="sxs-lookup"><span data-stu-id="2c400-105">A basic understanding of this error list will help you debug your applications by providing detailed information about the errors and suggesting possible solutions.</span></span>  
  
## <a name="the-design-time-error-list-interface"></a><span data-ttu-id="2c400-106">設計階段錯誤清單介面</span><span class="sxs-lookup"><span data-stu-id="2c400-106">The Design-Time Error List Interface</span></span>  
 <span data-ttu-id="2c400-107">如果 Windows Forms 設計工具載入失敗，錯誤清單會出現在設計工具中。</span><span class="sxs-lookup"><span data-stu-id="2c400-107">If the Windows Forms Designer fails to load, an error list will appear in the designer.</span></span> <span data-ttu-id="2c400-108">錯誤依分類分組。</span><span class="sxs-lookup"><span data-stu-id="2c400-108">The errors are grouped into categories.</span></span> <span data-ttu-id="2c400-109">比方說，如果您有四個未宣告的變數執行個體，這些會分組到相同的錯誤分類。</span><span class="sxs-lookup"><span data-stu-id="2c400-109">For example, if you have four instances of undeclared variables, these will be grouped into the same error category.</span></span> <span data-ttu-id="2c400-110">每個錯誤分類包含摘要說明此錯誤的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="2c400-110">Each error category includes a brief description that summarizes the error.</span></span>  
  
 <span data-ttu-id="2c400-111">您可以按一下錯誤分類標題，或按一下展開/摺疊 > 形箭號，以展開或摺疊錯誤分類。</span><span class="sxs-lookup"><span data-stu-id="2c400-111">You can expand or collapse an error category by either clicking on the error category heading or by clicking the expand/collapse chevron.</span></span> <span data-ttu-id="2c400-112">當您展開錯誤分類時，將會顯示下列額外說明︰</span><span class="sxs-lookup"><span data-stu-id="2c400-112">When you expand an error category, the following additional help is displayed:</span></span>  
  
-   <span data-ttu-id="2c400-113">此錯誤的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2c400-113">Instances of this error.</span></span>  
  
-   <span data-ttu-id="2c400-114">此錯誤的說明。</span><span class="sxs-lookup"><span data-stu-id="2c400-114">Help with this error.</span></span>  
  
-   <span data-ttu-id="2c400-115">此錯誤的相關論壇文章。</span><span class="sxs-lookup"><span data-stu-id="2c400-115">Forum posts about this error.</span></span>  
  
### <a name="instances-of-this-error"></a><span data-ttu-id="2c400-116">此錯誤的執行個體</span><span class="sxs-lookup"><span data-stu-id="2c400-116">Instances of This Error</span></span>  
 <span data-ttu-id="2c400-117">額外說明會列出目前專案中該錯誤的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="2c400-117">The additional help list all instances of the error in your current project.</span></span> <span data-ttu-id="2c400-118">許多錯誤包括確切的位置，格式如下︰[專案名稱] [表單名稱] 行︰[行號]資料行︰[資料行號碼]。</span><span class="sxs-lookup"><span data-stu-id="2c400-118">Many errors include an exact location in the following format: *[Project Name]* *[Form Name]* Line:*[Line Number]* Column:*[Column Number]*.</span></span> <span data-ttu-id="2c400-119">[移至程式碼] 連結將帶您前往程式碼中發生錯誤的位置。</span><span class="sxs-lookup"><span data-stu-id="2c400-119">The **Go to code** link takes you to the location in your code where the error occurs.</span></span>  
  
 <span data-ttu-id="2c400-120">如果錯誤有關聯的呼叫堆疊，您可以按一下 [呼叫堆疊顯示] 連結，進一步展開錯誤以顯示呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="2c400-120">If a call stack is associated with the error, you can click the **Show Call Stack** link, which further expands the error to show the call stack.</span></span> <span data-ttu-id="2c400-121">檢查堆疊可以提供寶貴的偵錯資訊。</span><span class="sxs-lookup"><span data-stu-id="2c400-121">Examining the stack can provide valuable debugging information.</span></span> <span data-ttu-id="2c400-122">例如，您可以追蹤發生錯誤之前所呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="2c400-122">For example, you can track the functions that were called before the error occurred.</span></span> <span data-ttu-id="2c400-123">您可以選取呼叫堆疊以複製並儲存。</span><span class="sxs-lookup"><span data-stu-id="2c400-123">The call stack is selectable so that you can copy and save it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c400-124">在 Visual Basic 中，設計階段錯誤清單不會顯示一個以上的錯誤，但可能顯示相同錯誤的多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="2c400-124">In Visual Basic, the design-time error list does not display more than one error, but it may display multiple instances of the same error.</span></span> <span data-ttu-id="2c400-125">在 Visual C++ 中，錯誤沒有 [移至程式碼] 連結/行號連結。</span><span class="sxs-lookup"><span data-stu-id="2c400-125">In Visual C++, the errors do not have goto code links/line number links.</span></span>  
  
### <a name="help-with-this-error"></a><span data-ttu-id="2c400-126">此錯誤的說明</span><span class="sxs-lookup"><span data-stu-id="2c400-126">Help with This Error</span></span>  
 <span data-ttu-id="2c400-127">如果錯誤包含關聯 MSDN 說明主題的連結，則額外說明會包含說明主題的連結。</span><span class="sxs-lookup"><span data-stu-id="2c400-127">If the error contains a link to an associated MSDN help topic, the additional help will include a link to the help topic.</span></span> <span data-ttu-id="2c400-128">當您按一下連結時，關聯的說明主題會出現在 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="2c400-128">When you click the link, the associated help topic appears in Visual Studio.</span></span>  
  
### <a name="forum-posts-about-this-error"></a><span data-ttu-id="2c400-129">此錯誤的相關論壇文章</span><span class="sxs-lookup"><span data-stu-id="2c400-129">Forum posts about this error</span></span>  
 <span data-ttu-id="2c400-130">額外說明包含與錯誤相關之 MSDN 論壇文章的連結。</span><span class="sxs-lookup"><span data-stu-id="2c400-130">The additional help will include a link to MSDN forum posts related to the error.</span></span> <span data-ttu-id="2c400-131">系統是根據錯誤訊息的字串來搜尋論壇。</span><span class="sxs-lookup"><span data-stu-id="2c400-131">The forums are searched based on the string of the error message.</span></span> <span data-ttu-id="2c400-132">您也可以嘗試搜尋下列論壇︰</span><span class="sxs-lookup"><span data-stu-id="2c400-132">You can also try searching the following forums:</span></span>  
  
-   [<span data-ttu-id="2c400-133">Windows Forms 設計工具論壇</span><span class="sxs-lookup"><span data-stu-id="2c400-133">Windows Forms Designer Forum</span></span>](https://go.microsoft.com/fwlink/?LinkId=203524)  
  
-   [<span data-ttu-id="2c400-134">Windows Forms 論壇</span><span class="sxs-lookup"><span data-stu-id="2c400-134">Windows Forms Forums</span></span>](https://go.microsoft.com/fwlink/?LinkId=203523)  
  
### <a name="ignore-and-continue"></a><span data-ttu-id="2c400-135">忽略並繼續</span><span class="sxs-lookup"><span data-stu-id="2c400-135">Ignore and Continue</span></span>  
 <span data-ttu-id="2c400-136">您可以選擇忽略錯誤狀況並繼續載入設計工具。</span><span class="sxs-lookup"><span data-stu-id="2c400-136">You can choose to ignore the error condition and continue loading the designer.</span></span> <span data-ttu-id="2c400-137">選擇此動作可能會導致非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="2c400-137">Choosing this action may result in unexpected behavior.</span></span> <span data-ttu-id="2c400-138">例如，控制項可能不會出現在設計介面上。</span><span class="sxs-lookup"><span data-stu-id="2c400-138">For example, controls may not appear on the design surface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c400-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c400-139">See Also</span></span>  
 [<span data-ttu-id="2c400-140">疑難排解設計階段開發</span><span class="sxs-lookup"><span data-stu-id="2c400-140">Troubleshooting Design-Time Development</span></span>](https://msdn.microsoft.com/library/e048d08e-fa7c-4be8-b238-4abaa199a0a6)  
 [<span data-ttu-id="2c400-141">針對控制項和元件撰寫進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="2c400-141">Troubleshooting Control and Component Authoring</span></span>](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 [<span data-ttu-id="2c400-142">在設計階段開發 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="2c400-142">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="2c400-143">Windows Forms 設計工具錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="2c400-143">Windows Forms Designer Error Messages</span></span>](https://msdn.microsoft.com/library/cf610bf4-5fe4-471c-bce7-6a05ece07bd2)
