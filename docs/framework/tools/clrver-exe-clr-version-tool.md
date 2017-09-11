---
title: "Clrver.exe (CLR 版本工具)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Clrver.exe
- CLR Version tool
ms.assetid: cbc2ee86-bdc8-4a65-a8f1-ba23bce3a699
caps.latest.revision: 13
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f8bef6f85f9e4b7d35e60c613a12ad87a26b70ab
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="clrverexe-clr-version-tool"></a><span data-ttu-id="6a2f7-102">Clrver.exe (CLR 版本工具)</span><span class="sxs-lookup"><span data-stu-id="6a2f7-102">Clrver.exe (CLR Version Tool)</span></span>
<span data-ttu-id="6a2f7-103">CLR 版本工具 (Clrver.exe) 會報告電腦上已安裝的所有通用語言執行平台 (CLR) 版本。</span><span class="sxs-lookup"><span data-stu-id="6a2f7-103">The CLR Version tool (Clrver.exe) reports all the installed versions of the common language runtime (CLR) on the computer.</span></span>  
  
 <span data-ttu-id="6a2f7-104">此工具會自動與 Visual Studio 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="6a2f7-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="6a2f7-105">若要執行此工具，請使用 [開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。</span><span class="sxs-lookup"><span data-stu-id="6a2f7-105">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="6a2f7-106">如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="6a2f7-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="6a2f7-107">在命令提示字元下輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="6a2f7-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a2f7-108">語法</span><span class="sxs-lookup"><span data-stu-id="6a2f7-108">Syntax</span></span>  
  
```  
clrver [option]  
```  
  
## <a name="options"></a><span data-ttu-id="6a2f7-109">選項</span><span class="sxs-lookup"><span data-stu-id="6a2f7-109">Options</span></span>  
  
|<span data-ttu-id="6a2f7-110">選項</span><span class="sxs-lookup"><span data-stu-id="6a2f7-110">Option</span></span>|<span data-ttu-id="6a2f7-111">說明</span><span class="sxs-lookup"><span data-stu-id="6a2f7-111">Description</span></span>|  
|------------|-----------------|  
|`-all`|<span data-ttu-id="6a2f7-112">顯示電腦上所有正在使用 CLR 的處理序。</span><span class="sxs-lookup"><span data-stu-id="6a2f7-112">Displays all processes on the computer that are using the CLR.</span></span>|  
|<span data-ttu-id="6a2f7-113">*pid*</span><span class="sxs-lookup"><span data-stu-id="6a2f7-113">*pid*</span></span>|<span data-ttu-id="6a2f7-114">顯示具有指定處理序 ID (PID) 的處理序所使用的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="6a2f7-114">Displays the version(s) of the CLR used by the process that has the specified process ID (PID).</span></span>|  
|`-?`|<span data-ttu-id="6a2f7-115">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="6a2f7-115">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a2f7-116">備註</span><span class="sxs-lookup"><span data-stu-id="6a2f7-116">Remarks</span></span>  
 <span data-ttu-id="6a2f7-117">如果您呼叫 Clrver.exe 時未使用任何選項，則會顯示所有已安裝的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="6a2f7-117">If you call Clrver.exe with no options, it displays all installed CLR versions.</span></span> <span data-ttu-id="6a2f7-118">如果您指定另一個使用者的 PID，則必須具有系統管理權限才能取得版本資訊。</span><span class="sxs-lookup"><span data-stu-id="6a2f7-118">If you specify a PID for another user, you must have administrative permissions to obtain the version information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6a2f7-119">在 Windows Vista (含) 以後版本中，使用者帳戶控制 (UAC) 會判斷使用者的權限。</span><span class="sxs-lookup"><span data-stu-id="6a2f7-119">In Windows Vista and later, User Account Control (UAC) determines the privileges of a user.</span></span> <span data-ttu-id="6a2f7-120">如果您是內建 Administrators 群組的成員，系統會將兩個執行階段存取語彙基元 (Token) 指派給您：標準使用者存取語彙基元及管理員存取語彙基元。</span><span class="sxs-lookup"><span data-stu-id="6a2f7-120">If you are a member of the Built-in Administrators group, you are assigned two run-time access tokens: a standard user access token and an administrator access token.</span></span> <span data-ttu-id="6a2f7-121">根據預設，您會屬於標準使用者角色。</span><span class="sxs-lookup"><span data-stu-id="6a2f7-121">By default, you are in the standard user role.</span></span> <span data-ttu-id="6a2f7-122">若要執行需要系統管理權限的程式碼，您必須先將權限從標準使用者提高為系統管理員。</span><span class="sxs-lookup"><span data-stu-id="6a2f7-122">To execute code that requires administrative permission, you must first elevate your privileges from standard user to administrator.</span></span> <span data-ttu-id="6a2f7-123">您可以在啟動命令提示字元時以滑鼠右鍵按一下命令提示字元圖示，並表示您要以系統管理員身分執行，藉此提高為系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="6a2f7-123">You can do this when you start the command prompt by right-clicking the command prompt icon and indicating that you want to run as an administrator.</span></span>  
  
 <span data-ttu-id="6a2f7-124">若您嘗試判斷 SYSTEM、LOCAL SERVICE 和 NETWORK SERVICE 處理序的 CLR 版本，系統會顯示一則訊息，表示 PID 不存在。</span><span class="sxs-lookup"><span data-stu-id="6a2f7-124">Attempting to determine the CLR version for SYSTEM, LOCAL SERVICE, and NETWORK SERVICE processes results in a message indicating that the PID doesn't exist.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="6a2f7-125">範例</span><span class="sxs-lookup"><span data-stu-id="6a2f7-125">Examples</span></span>  
 <span data-ttu-id="6a2f7-126">下列命令會顯示電腦上安裝的所有 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="6a2f7-126">The following command displays all the versions of the CLR installed on the computer.</span></span>  
  
 `clrver`  
  
 <span data-ttu-id="6a2f7-127">下列命令會顯示處理序 128 所使用的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="6a2f7-127">The following command displays the version of the CLR used by process 128.</span></span>  
  
 `clrver 128`  
  
 <span data-ttu-id="6a2f7-128">下列命令會顯示所有 Managed 處理序及其使用的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="6a2f7-128">The following command displays all the managed processes and the version of the CLR they are using.</span></span>  
  
 `Clrver -all`  
  
## <a name="see-also"></a><span data-ttu-id="6a2f7-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a2f7-129">See Also</span></span>  
 <span data-ttu-id="6a2f7-130">[工具](../../../docs/framework/tools/index.md) </span><span class="sxs-lookup"><span data-stu-id="6a2f7-130">[Tools](../../../docs/framework/tools/index.md) </span></span>  
 [<span data-ttu-id="6a2f7-131">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="6a2f7-131">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

