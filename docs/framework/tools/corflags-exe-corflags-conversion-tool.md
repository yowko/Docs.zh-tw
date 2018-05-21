---
title: CorFlags.exe (CorFlags 轉換工具)
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4a5b6d490387f2da441ad95bdf369f700cf2e9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="70486-102">CorFlags.exe (CorFlags 轉換工具)</span><span class="sxs-lookup"><span data-stu-id="70486-102">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="70486-103">CorFlags 轉換工具可讓您設定可攜式執行映像標頭的 CorFlags 區段。</span><span class="sxs-lookup"><span data-stu-id="70486-103">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="70486-104">此工具會自動與 Visual Studio 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="70486-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="70486-105">若要執行此工具，請使用 [開發人員命令提示字元] \(或 Windows 7 中的 [Visual Studio 命令提示字元])。</span><span class="sxs-lookup"><span data-stu-id="70486-105">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="70486-106">如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="70486-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="70486-107">在命令提示字元下輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="70486-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70486-108">語法</span><span class="sxs-lookup"><span data-stu-id="70486-108">Syntax</span></span>  
  
```  
CorFlags.exe assembly [options]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="70486-109">參數</span><span class="sxs-lookup"><span data-stu-id="70486-109">Parameters</span></span>  
  
|<span data-ttu-id="70486-110">必要參數</span><span class="sxs-lookup"><span data-stu-id="70486-110">Required parameter</span></span>|<span data-ttu-id="70486-111">描述</span><span class="sxs-lookup"><span data-stu-id="70486-111">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="70486-112">要設定其 CorFlags 的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="70486-112">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="70486-113">選項</span><span class="sxs-lookup"><span data-stu-id="70486-113">Option</span></span>|<span data-ttu-id="70486-114">描述</span><span class="sxs-lookup"><span data-stu-id="70486-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="70486-115">**/32BIT[REQ]+**</span><span class="sxs-lookup"><span data-stu-id="70486-115">**/32BIT[REQ]+**</span></span>|<span data-ttu-id="70486-116">設定 32BITREQUIRED 旗標。</span><span class="sxs-lookup"><span data-stu-id="70486-116">Sets the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="70486-117">**/32BIT[REQ]-**</span><span class="sxs-lookup"><span data-stu-id="70486-117">**/32BIT[REQ]-**</span></span>|<span data-ttu-id="70486-118">清除 32BITREQUIRED 旗標。</span><span class="sxs-lookup"><span data-stu-id="70486-118">Clears the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="70486-119">**/32BITPREF+**</span><span class="sxs-lookup"><span data-stu-id="70486-119">**/32BITPREF+**</span></span>|<span data-ttu-id="70486-120">設定 32BITPREFERRED 旗標。</span><span class="sxs-lookup"><span data-stu-id="70486-120">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="70486-121">應用程式在 64 位元平台上仍然以 32 位元處理序執行。</span><span class="sxs-lookup"><span data-stu-id="70486-121">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="70486-122">請只對 EXE 檔案設定這個旗標。</span><span class="sxs-lookup"><span data-stu-id="70486-122">Set this flag only on EXE files.</span></span> <span data-ttu-id="70486-123">如果在 DLL 上設定這個旗標，DLL 就無法在 64 位元處理序中載入，如此就會擲回 <xref:System.BadImageFormatException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="70486-123">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="70486-124">具有這個旗標的 EXE 檔案可以載入至 64 位元處理序。</span><span class="sxs-lookup"><span data-stu-id="70486-124">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="70486-125">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 的新功能。</span><span class="sxs-lookup"><span data-stu-id="70486-125">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|<span data-ttu-id="70486-126">**/32BITPREF-**</span><span class="sxs-lookup"><span data-stu-id="70486-126">**/32BITPREF-**</span></span>|<span data-ttu-id="70486-127">清除 32BITPREFERRED 旗標。</span><span class="sxs-lookup"><span data-stu-id="70486-127">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="70486-128">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 的新功能。</span><span class="sxs-lookup"><span data-stu-id="70486-128">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|<span data-ttu-id="70486-129">**/?**</span><span class="sxs-lookup"><span data-stu-id="70486-129">**/?**</span></span>|<span data-ttu-id="70486-130">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="70486-130">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="70486-131">**/Force**</span><span class="sxs-lookup"><span data-stu-id="70486-131">**/Force**</span></span>|<span data-ttu-id="70486-132">即使組件採用強式名稱，仍然強制進行更新。</span><span class="sxs-lookup"><span data-stu-id="70486-132">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="70486-133">**重要事項：** 如果您更新強式名稱組件，就必須先再次簽署該組件，再執行其程式碼。</span><span class="sxs-lookup"><span data-stu-id="70486-133">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|<span data-ttu-id="70486-134">**/help**</span><span class="sxs-lookup"><span data-stu-id="70486-134">**/help**</span></span>|<span data-ttu-id="70486-135">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="70486-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="70486-136">**/ILONLY+**</span><span class="sxs-lookup"><span data-stu-id="70486-136">**/ILONLY+**</span></span>|<span data-ttu-id="70486-137">設定 ILONLY 旗標。</span><span class="sxs-lookup"><span data-stu-id="70486-137">Sets the ILONLY flag.</span></span>|  
|<span data-ttu-id="70486-138">**/ILONLY-**</span><span class="sxs-lookup"><span data-stu-id="70486-138">**/ILONLY-**</span></span>|<span data-ttu-id="70486-139">清除 ILONLY 旗標。</span><span class="sxs-lookup"><span data-stu-id="70486-139">Clears the ILONLY flag.</span></span>|  
|<span data-ttu-id="70486-140">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="70486-140">**/nologo**</span></span>|<span data-ttu-id="70486-141">隱藏 Microsoft 程式啟始資訊顯示。</span><span class="sxs-lookup"><span data-stu-id="70486-141">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="70486-142">**/RevertCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="70486-142">**/RevertCLRHeader**</span></span>|<span data-ttu-id="70486-143">將 CLR 標頭版本還原為 2.0。</span><span class="sxs-lookup"><span data-stu-id="70486-143">Reverts the CLR header version to 2.0.</span></span>|  
|<span data-ttu-id="70486-144">**/UpgradeCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="70486-144">**/UpgradeCLRHeader**</span></span>|<span data-ttu-id="70486-145">將 CLR 標頭版本升級到 2.5。</span><span class="sxs-lookup"><span data-stu-id="70486-145">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="70486-146">**注意：** 組件的 CLR 標頭必須是 2.5 (含) 以上版本，才能以原本的形式執行。</span><span class="sxs-lookup"><span data-stu-id="70486-146">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70486-147">備註</span><span class="sxs-lookup"><span data-stu-id="70486-147">Remarks</span></span>  
 <span data-ttu-id="70486-148">如果未指定任何選項，則 CorFlags 轉換工具會針對所指定組件顯示旗標。</span><span class="sxs-lookup"><span data-stu-id="70486-148">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70486-149">請參閱</span><span class="sxs-lookup"><span data-stu-id="70486-149">See Also</span></span>  
 [<span data-ttu-id="70486-150">工具</span><span class="sxs-lookup"><span data-stu-id="70486-150">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="70486-151">64 位元應用程式</span><span class="sxs-lookup"><span data-stu-id="70486-151">64-bit Applications</span></span>](../../../docs/framework/64-bit-apps.md)  
 [<span data-ttu-id="70486-152">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="70486-152">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
