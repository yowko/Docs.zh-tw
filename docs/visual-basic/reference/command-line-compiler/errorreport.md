---
title: "/errorreport |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c2f9a9daf6aed6348baeb2c4de2fe5caef70f52b
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="errorreport"></a><span data-ttu-id="beca6-102">/errorreport</span><span class="sxs-lookup"><span data-stu-id="beca6-102">/errorreport</span></span>
<span data-ttu-id="beca6-103">指定 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 編譯器報告編譯器內部錯誤的方式。</span><span class="sxs-lookup"><span data-stu-id="beca6-103">Specifies how the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler should report internal compiler errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beca6-104">語法</span><span class="sxs-lookup"><span data-stu-id="beca6-104">Syntax</span></span>  
  
```  
/errorreport:{ prompt | queue | send | none }  
```  
  
## <a name="remarks"></a><span data-ttu-id="beca6-105">備註</span><span class="sxs-lookup"><span data-stu-id="beca6-105">Remarks</span></span>  
 <span data-ttu-id="beca6-106">此選項提供便利的方式來報告[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器內部錯誤 (ICE) [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] Microsoft 小組。</span><span class="sxs-lookup"><span data-stu-id="beca6-106">This option provides a convenient way to report a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] internal compiler error (ICE) to the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] team at Microsoft.</span></span> <span data-ttu-id="beca6-107">根據預設，編譯器會將任何資訊傳送到 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="beca6-107">By default, the compiler sends no information to Microsoft.</span></span> <span data-ttu-id="beca6-108">不過，如果發生編譯器內部錯誤，此選項可讓您向 Microsoft 回報錯誤。</span><span class="sxs-lookup"><span data-stu-id="beca6-108">However, if you do encounter an internal compiler error, this option allows you to report the error to Microsoft.</span></span> <span data-ttu-id="beca6-109">這項資訊可協助 Microsoft 工程師找出原因，而且可能有助於改善的下一個版本[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="beca6-109">That information will help Microsoft engineers identify the cause and may help improve the next release of [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
 <span data-ttu-id="beca6-110">傳送報表的使用者的能力取決於電腦和使用者原則權限。</span><span class="sxs-lookup"><span data-stu-id="beca6-110">A user's ability to send reports depends on machine and user policy permissions.</span></span>  
  
 <span data-ttu-id="beca6-111">下表摘要說明的效果`/errorreport`選項。</span><span class="sxs-lookup"><span data-stu-id="beca6-111">The following table summarizes the effect of the `/errorreport` option.</span></span>  
  
|<span data-ttu-id="beca6-112">選項</span><span class="sxs-lookup"><span data-stu-id="beca6-112">Option</span></span>|<span data-ttu-id="beca6-113">行為</span><span class="sxs-lookup"><span data-stu-id="beca6-113">Behavior</span></span>|  
|---|---|  
|`prompt`|<span data-ttu-id="beca6-114">如果發生編譯器內部錯誤，對話方塊隨即出現，讓您可以檢視編譯器所收集的確切資料。</span><span class="sxs-lookup"><span data-stu-id="beca6-114">If an internal compiler error occurs, a dialog box comes up so that you can view the exact data that the compiler collected.</span></span> <span data-ttu-id="beca6-115">您可以判斷是否有任何錯誤報表中的機密資訊，並決定是否要傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="beca6-115">You can determine if there is any sensitive information in the error report and make a decision on whether to send it to Microsoft.</span></span> <span data-ttu-id="beca6-116">如果您決定要傳送，而且電腦和使用者原則設定可讓它，編譯器會將資料傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="beca6-116">If you decide to send it, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span>|  
|`queue`|<span data-ttu-id="beca6-117">錯誤報告排入佇列。</span><span class="sxs-lookup"><span data-stu-id="beca6-117">Queues the error report.</span></span> <span data-ttu-id="beca6-118">當您登入系統管理員權限時，您可以在上次登入報告任何失敗 （將不會提示您要傳送報告的失敗一次以上每隔三天）。</span><span class="sxs-lookup"><span data-stu-id="beca6-118">When you log in with administrator privileges, you can report any failures since the last time you were logged in (you will not be prompted to send reports for failures more than once every three days).</span></span> <span data-ttu-id="beca6-119">這是預設行為時`/errorreport`未指定選項。</span><span class="sxs-lookup"><span data-stu-id="beca6-119">This is the default behavior when the `/errorreport` option is not specified.</span></span>|  
|`send`|<span data-ttu-id="beca6-120">如果發生編譯器內部錯誤，而且電腦和使用者原則設定可讓它，編譯器會將資料傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="beca6-120">If an internal compiler error occurs, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span><br /><br /> <span data-ttu-id="beca6-121">選擇`/errorReport:send`會嘗試自動傳送給 Microsoft 的資訊時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="beca6-121">The option `/errorReport:send` attempts to automatically send error information to Microsoft.</span></span> <span data-ttu-id="beca6-122">此選項取決於登錄中。</span><span class="sxs-lookup"><span data-stu-id="beca6-122">This option depends on the registry.</span></span> <span data-ttu-id="beca6-123">如需在登錄中設定適當的值的詳細資訊，請參閱[如何開啟自動錯誤報告在 Visual Studio 2008 命令列工具](http://go.microsoft.com/fwlink/?LinkID=184695)。</span><span class="sxs-lookup"><span data-stu-id="beca6-123">For more information about setting the appropriate values in the registry, see [How to Turn on Automatic Error Reporting in Visual Studio 2008 Command-line Tools](http://go.microsoft.com/fwlink/?LinkID=184695).</span></span>|  
|`none`|<span data-ttu-id="beca6-124">發生內部編譯器錯誤時，它將不會收集或傳送到 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="beca6-124">If an internal compiler error occurs, it will not be collected or sent to Microsoft.</span></span>|  
  
 <span data-ttu-id="beca6-125">編譯器會傳送資料，包括堆疊時的錯誤，通常包括一些原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="beca6-125">The compiler sends data that includes the stack at the time of the error, which usually includes some source code.</span></span> <span data-ttu-id="beca6-126">如果`/errorreport`搭配[/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)選項，則會傳送整個原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="beca6-126">If `/errorreport` is used with the [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, then the entire source file is sent.</span></span>  
  
 <span data-ttu-id="beca6-127">這個選項最適合搭配[/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)選項，因為它可讓 Microsoft 工程師更輕鬆地重現錯誤。</span><span class="sxs-lookup"><span data-stu-id="beca6-127">This option is best used with the [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, because it allows Microsoft engineers to more easily reproduce the error.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="beca6-128">`/errorreport`選項不是從 Visual Studio 開發環境中使用，可從命令列編譯時，才。</span><span class="sxs-lookup"><span data-stu-id="beca6-128">The `/errorreport` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="beca6-129">範例</span><span class="sxs-lookup"><span data-stu-id="beca6-129">Example</span></span>  
 <span data-ttu-id="beca6-130">下列程式碼會嘗試編譯`T2.vb`，而且如果編譯器遇到內部編譯器錯誤，它會提示您傳送錯誤報告給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="beca6-130">The following code attempts to compile `T2.vb`, and if the compiler encounters an internal compiler error, it prompts you to send the error report to Microsoft.</span></span>  
  
```  
vbc /errorreport:prompt t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="beca6-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="beca6-131">See Also</span></span>  
 <span data-ttu-id="beca6-132">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="beca6-132">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="beca6-133"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="beca6-133"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="beca6-134"> [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)</span><span class="sxs-lookup"><span data-stu-id="beca6-134"> [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)</span></span>
