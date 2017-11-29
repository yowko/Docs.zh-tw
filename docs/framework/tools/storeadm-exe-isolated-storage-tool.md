---
title: "Storeadm.exe (隔離儲存區工具)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Storeadm.exe
- listing stores for current user
- Isolated Storage tool
- stores, current user
- removing stores
ms.assetid: b81202b8-d91d-4b23-9c53-4a112f74a44a
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d9ae6b007fe32dfbef973105311ba929cc247e6b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="storeadmexe-isolated-storage-tool"></a><span data-ttu-id="68096-102">Storeadm.exe (隔離儲存區工具)</span><span class="sxs-lookup"><span data-stu-id="68096-102">Storeadm.exe (Isolated Storage Tool)</span></span>
<span data-ttu-id="68096-103">隔離儲存區 (Isolated Storage) 工具可以列出或移除目前使用者的所有現有存放區。</span><span class="sxs-lookup"><span data-stu-id="68096-103">The Isolated Storage tool lists or removes all existing stores for the current user.</span></span>  
  
 <span data-ttu-id="68096-104">此工具會自動與 Visual Studio 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="68096-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="68096-105">若要執行此工具，請使用 [開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。</span><span class="sxs-lookup"><span data-stu-id="68096-105">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="68096-106">如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="68096-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="68096-107">在命令提示字元下輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="68096-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68096-108">語法</span><span class="sxs-lookup"><span data-stu-id="68096-108">Syntax</span></span>  
  
```  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68096-109">參數</span><span class="sxs-lookup"><span data-stu-id="68096-109">Parameters</span></span>  
  
|<span data-ttu-id="68096-110">選項</span><span class="sxs-lookup"><span data-stu-id="68096-110">Option</span></span>|<span data-ttu-id="68096-111">說明</span><span class="sxs-lookup"><span data-stu-id="68096-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="68096-112">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="68096-112">**/h**[**elp**]</span></span>|<span data-ttu-id="68096-113">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="68096-113">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="68096-114">**/list**</span><span class="sxs-lookup"><span data-stu-id="68096-114">**/list**</span></span>|<span data-ttu-id="68096-115">顯示目前使用者的所有現有存放區。</span><span class="sxs-lookup"><span data-stu-id="68096-115">Displays all existing stores for the current user.</span></span> <span data-ttu-id="68096-116">包括這個使用者所執行的所有應用程式或組件的存放區。</span><span class="sxs-lookup"><span data-stu-id="68096-116">This includes the stores for all applications or assemblies executed by this user.</span></span>|  
|<span data-ttu-id="68096-117">**/machine**</span><span class="sxs-lookup"><span data-stu-id="68096-117">**/machine**</span></span>|<span data-ttu-id="68096-118">選取電腦存放區。</span><span class="sxs-lookup"><span data-stu-id="68096-118">Selects the machine store.</span></span> <span data-ttu-id="68096-119">使用這個選項搭配 **/list** 或 **/remove** 選項，可指定動作應該套用至電腦存放區。</span><span class="sxs-lookup"><span data-stu-id="68096-119">Use this option with the **/list** or **/remove** option to specify that the action should apply to the machine store.</span></span><br /><br /> <span data-ttu-id="68096-120">.NET Framework 2.0 的新功能</span><span class="sxs-lookup"><span data-stu-id="68096-120">New in the .NET Framework 2.0</span></span>|  
|<span data-ttu-id="68096-121">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="68096-121">**/quiet**</span></span>|<span data-ttu-id="68096-122">指定無訊息模式，隱藏資訊輸出，以便僅顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="68096-122">Specifies quiet mode; suppresses informational output so that only error messages appear.</span></span>|  
|<span data-ttu-id="68096-123">**/remove**</span><span class="sxs-lookup"><span data-stu-id="68096-123">**/remove**</span></span>|<span data-ttu-id="68096-124">永久移除目前使用者的所有現有存放區。</span><span class="sxs-lookup"><span data-stu-id="68096-124">Permanently removes all existing stores for the current user.</span></span>|  
|<span data-ttu-id="68096-125">**/roaming**</span><span class="sxs-lookup"><span data-stu-id="68096-125">**/roaming**</span></span>|<span data-ttu-id="68096-126">選取漫遊存放區。</span><span class="sxs-lookup"><span data-stu-id="68096-126">Selects the roaming store.</span></span> <span data-ttu-id="68096-127">使用這個選項搭配 **/list** 或 **/remove** 選項，可指定動作應該套用至漫遊存放區。</span><span class="sxs-lookup"><span data-stu-id="68096-127">Use this option with the **/list** or **/remove** options to specify that the action should apply to the roaming store.</span></span>|  
|<span data-ttu-id="68096-128">**/?**</span><span class="sxs-lookup"><span data-stu-id="68096-128">**/?**</span></span>|<span data-ttu-id="68096-129">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="68096-129">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68096-130">備註</span><span class="sxs-lookup"><span data-stu-id="68096-130">Remarks</span></span>  
 <span data-ttu-id="68096-131">從命令列執行 Storeadm.exe 而沒有指定任何選項時，會顯示工具的語法和選項。</span><span class="sxs-lookup"><span data-stu-id="68096-131">Running Storeadm.exe from the command line without specifying any options displays the syntax and options for the tool.</span></span>  
  
 <span data-ttu-id="68096-132">**/list** 和 **/remove** 選項通常不會同時使用；不過，如果指定了兩個以上的選項，則會依照出現在命令列上的順序執行這些選項。</span><span class="sxs-lookup"><span data-stu-id="68096-132">The **/list** and **/remove** options are typically used one at a time; however, if two or more options are specified they will be performed in the order in which they appear on the command line.</span></span>  
  
 <span data-ttu-id="68096-133">應用程式可以選擇儲存至使用者的兩個存放區之一，或是儲存至電腦存放區：</span><span class="sxs-lookup"><span data-stu-id="68096-133">Applications have a choice of saving to one of two stores for a user or to the machine store:</span></span>  
  
-   <span data-ttu-id="68096-134">本機存放區位於保證不漫遊的位置 (在 Windows 2000 (含) 以後版本上)，即使已啟用該使用者的使用者資料漫遊也一樣。</span><span class="sxs-lookup"><span data-stu-id="68096-134">The local store exists in a location that is guaranteed not to roam (on Windows 2000 and later) even if user data roaming is enabled for the user.</span></span>  
  
-   <span data-ttu-id="68096-135">漫遊存放區位於能夠漫遊的位置，不過必須先透過 Windows NT 系統管理啟用使用者的漫遊功能才能進行漫遊。</span><span class="sxs-lookup"><span data-stu-id="68096-135">The roaming store exists in a location that is able to roam, but can only do so if roaming is enabled for the user via Windows NT administration.</span></span>  
  
-   <span data-ttu-id="68096-136">電腦存放區為電腦上所有使用者通用，並且存放在該電腦的通用目錄下。</span><span class="sxs-lookup"><span data-stu-id="68096-136">The machine store is common to all users on a machine and is stored under a common directory on that machine.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="68096-137">電腦存放區是 .NET Framework 2.0 版中的新功能。</span><span class="sxs-lookup"><span data-stu-id="68096-137">The machine store is new in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="68096-138">使用者的漫遊實際上是否啟用，並不會影響 Storeadm.exe 的系統管理。</span><span class="sxs-lookup"><span data-stu-id="68096-138">Whether roaming is actually enabled for the user does not affect the administration of Storeadm.exe.</span></span> <span data-ttu-id="68096-139">執行該工具而沒有使用任何選項時，會將所有動作套用至本機存放區。</span><span class="sxs-lookup"><span data-stu-id="68096-139">Running the tool without any options applies all actions to the local store.</span></span> <span data-ttu-id="68096-140">執行該工具搭配 **/roaming** 選項時，會將所有動作套用至能夠漫遊的存放區。</span><span class="sxs-lookup"><span data-stu-id="68096-140">Running the tool with the **/roaming** option applies all actions to the store that is able to roam.</span></span> <span data-ttu-id="68096-141">執行該工具搭配 **/machine** 選項時，會將所有動作套用至電腦存放區。</span><span class="sxs-lookup"><span data-stu-id="68096-141">Running the tool with the **/machine** option applies all actions to the machine store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68096-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68096-142">See Also</span></span>  
 [<span data-ttu-id="68096-143">工具</span><span class="sxs-lookup"><span data-stu-id="68096-143">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="68096-144">隔離儲存區</span><span class="sxs-lookup"><span data-stu-id="68096-144">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)  
 [<span data-ttu-id="68096-145">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="68096-145">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
