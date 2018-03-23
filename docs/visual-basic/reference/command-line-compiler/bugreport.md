---
title: -bugreport
ms.date: 03/08/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 766a4252fd77be95e2641239cba53a4d90e0cb1d
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="-bugreport"></a><span data-ttu-id="44c5f-102">-bugreport</span><span class="sxs-lookup"><span data-stu-id="44c5f-102">-bugreport</span></span>
<span data-ttu-id="44c5f-103">建立檔案錯誤報告時，您可以使用的檔案。</span><span class="sxs-lookup"><span data-stu-id="44c5f-103">Creates a file that you can use when you file a bug report.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44c5f-104">語法</span><span class="sxs-lookup"><span data-stu-id="44c5f-104">Syntax</span></span>  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="44c5f-105">引數</span><span class="sxs-lookup"><span data-stu-id="44c5f-105">Arguments</span></span>  
  
|<span data-ttu-id="44c5f-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="44c5f-106">Term</span></span>|<span data-ttu-id="44c5f-107">定義</span><span class="sxs-lookup"><span data-stu-id="44c5f-107">Definition</span></span>|  
|---|---|  
|`file`|<span data-ttu-id="44c5f-108">必要。</span><span class="sxs-lookup"><span data-stu-id="44c5f-108">Required.</span></span> <span data-ttu-id="44c5f-109">將包含錯誤報告的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="44c5f-109">The name of the file that will contain your bug report.</span></span> <span data-ttu-id="44c5f-110">將檔案名稱括在引號 ("") 如果名稱包含空格。</span><span class="sxs-lookup"><span data-stu-id="44c5f-110">Enclose the file name in quotation marks (" ") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44c5f-111">備註</span><span class="sxs-lookup"><span data-stu-id="44c5f-111">Remarks</span></span>  
 <span data-ttu-id="44c5f-112">下列資訊加入至`file`:</span><span class="sxs-lookup"><span data-stu-id="44c5f-112">The following information is added to `file`:</span></span>  
  
-   <span data-ttu-id="44c5f-113">在編譯中的所有原始程式檔的複本。</span><span class="sxs-lookup"><span data-stu-id="44c5f-113">A copy of all source-code files in the compilation.</span></span>  
  
-   <span data-ttu-id="44c5f-114">在編譯中使用的編譯器選項的清單。</span><span class="sxs-lookup"><span data-stu-id="44c5f-114">A list of the compiler options used in the compilation.</span></span>  
  
-   <span data-ttu-id="44c5f-115">您的編譯器、 通用語言執行平台，以及作業系統的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="44c5f-115">Version information about your compiler, common language runtime, and operating system.</span></span>  
  
-   <span data-ttu-id="44c5f-116">編譯器輸出 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="44c5f-116">Compiler output, if any.</span></span>  
  
-   <span data-ttu-id="44c5f-117">此問題，會提示您輸入的描述。</span><span class="sxs-lookup"><span data-stu-id="44c5f-117">A description of the problem, for which you are prompted.</span></span>  
  
-   <span data-ttu-id="44c5f-118">描述如何在您認為問題應該固定，會提示您輸入。</span><span class="sxs-lookup"><span data-stu-id="44c5f-118">A description of how you think the problem should be fixed, for which you are prompted.</span></span>  
  
 <span data-ttu-id="44c5f-119">因為所有的原始程式檔的複本包含在`file`，您可能想要重新產生在最短的程式 （可能） 程式碼缺失。</span><span class="sxs-lookup"><span data-stu-id="44c5f-119">Because a copy of all source-code files is included in `file`, you may want to reproduce the (suspected) code defect in the shortest possible program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="44c5f-120">`-bugreport`選項會產生包含潛在的敏感資訊的檔案。</span><span class="sxs-lookup"><span data-stu-id="44c5f-120">The `-bugreport` option produces a file that contains potentially sensitive information.</span></span> <span data-ttu-id="44c5f-121">這包括目前的時間，編譯器版本[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]版本、 作業系統版本、 使用者名稱、 命令列引數，編譯器已執行，所有的原始程式碼，而且的二進位格式的任何參考的組件。</span><span class="sxs-lookup"><span data-stu-id="44c5f-121">This includes current time, compiler version, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] version, OS version, user name, the command-line arguments with which the compiler was run, all source code, and the binary form of any referenced assembly.</span></span> <span data-ttu-id="44c5f-122">這個選項可以存取的伺服器端編譯的 Web.config 檔案中指定命令列選項[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="44c5f-122">This option can be accessed by specifying command-line options in the Web.config file for a server-side compilation of an [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] application.</span></span> <span data-ttu-id="44c5f-123">若要防止這個情況，修改 Machine.config 檔案，不允許使用者從伺服器上進行編譯。</span><span class="sxs-lookup"><span data-stu-id="44c5f-123">To prevent this, modify the Machine.config file to disallow users from compiling on the server.</span></span>  
  
 <span data-ttu-id="44c5f-124">如果此選項搭配`-errorreport:prompt`， `-errorreport:queue`，或`-errorreport:send`，和您的應用程式發生編譯器內部錯誤中的資訊`file`傳送給 Microsoft Corporation。</span><span class="sxs-lookup"><span data-stu-id="44c5f-124">If this option is used with `-errorreport:prompt`, `-errorreport:queue`, or `-errorreport:send`, and your application encounters an internal compiler error, the information in `file` is sent to Microsoft Corporation.</span></span> <span data-ttu-id="44c5f-125">該資訊可協助 Microsoft 工程師找出錯誤的原因，而且可能有助於改善的下一個版本[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="44c5f-125">That information will help Microsoft engineers identify the cause of the error and may help improve the next release of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="44c5f-126">根據預設，會不傳送任何資訊給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="44c5f-126">By default, no information is sent to Microsoft.</span></span> <span data-ttu-id="44c5f-127">不過，當您編譯應用程式使用`-errorreport:queue`，預設會啟用它，應用程式收集的錯誤報表。</span><span class="sxs-lookup"><span data-stu-id="44c5f-127">However, when you compile an application by using `-errorreport:queue`, which is enabled by default, the application collects its error reports.</span></span> <span data-ttu-id="44c5f-128">然後，當電腦的系統管理員登入時，錯誤報告系統就會顯示快顯視窗，可讓系統管理員以轉寄給 Microsoft 報告任何錯誤發生在登入。</span><span class="sxs-lookup"><span data-stu-id="44c5f-128">Then, when the computer's administrator logs in, the error reporting system displays a pop-up window that enables the administrator to forward to Microsoft any error reports that occurred since the logon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44c5f-129">`/bugreport`選項不是從 Visual Studio 開發環境中使用，則可以使用只有當您編譯從命令列。</span><span class="sxs-lookup"><span data-stu-id="44c5f-129">The `/bugreport` option is not available from within the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44c5f-130">範例</span><span class="sxs-lookup"><span data-stu-id="44c5f-130">Example</span></span>  
 <span data-ttu-id="44c5f-131">下列範例會編譯`T2.vb`並放入檔案中的所有 bug 報告資訊`Problem.txt`。</span><span class="sxs-lookup"><span data-stu-id="44c5f-131">The following example compiles `T2.vb` and puts all bug-reporting information in the file `Problem.txt`.</span></span>  
  
```  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="44c5f-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44c5f-132">See Also</span></span>  
 [<span data-ttu-id="44c5f-133">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="44c5f-133">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="44c5f-134">-偵錯 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44c5f-134">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [<span data-ttu-id="44c5f-135">-errorreport</span><span class="sxs-lookup"><span data-stu-id="44c5f-135">-errorreport</span></span>](../../../visual-basic/reference/command-line-compiler/errorreport.md)  
 [<span data-ttu-id="44c5f-136">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="44c5f-136">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="44c5f-137">securityPolicy （ASP.NET 設定結構描述） 的 trustLevel 項目</span><span class="sxs-lookup"><span data-stu-id="44c5f-137">trustLevel Element for securityPolicy (ASP.NET Settings Schema)</span></span>](http://msdn.microsoft.com/library/729ab04c-03da-4ee5-86b1-be9d08a09369)
