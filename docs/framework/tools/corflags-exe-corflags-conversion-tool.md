---
title: CorFlags.exe (CorFlags 轉換工具)
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
ms.openlocfilehash: e1251b6660db45f3af4f6e57114b1b10da18bd0a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73129854"
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="50b3f-102">CorFlags.exe (CorFlags 轉換工具)</span><span class="sxs-lookup"><span data-stu-id="50b3f-102">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="50b3f-103">CorFlags 轉換工具可讓您設定可攜式執行映像標頭的 CorFlags 區段。</span><span class="sxs-lookup"><span data-stu-id="50b3f-103">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="50b3f-104">此工具會自動與 Visual Studio 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="50b3f-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="50b3f-105">若要執行這項工具，請使用 [Visual Studio 開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。</span><span class="sxs-lookup"><span data-stu-id="50b3f-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="50b3f-106">如需詳細資訊，請參閱[命令提示字元](developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="50b3f-106">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="50b3f-107">在命令提示字元中，請輸入下列項目：</span><span class="sxs-lookup"><span data-stu-id="50b3f-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50b3f-108">語法</span><span class="sxs-lookup"><span data-stu-id="50b3f-108">Syntax</span></span>  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="50b3f-109">參數</span><span class="sxs-lookup"><span data-stu-id="50b3f-109">Parameters</span></span>  
  
|<span data-ttu-id="50b3f-110">必要參數</span><span class="sxs-lookup"><span data-stu-id="50b3f-110">Required parameter</span></span>|<span data-ttu-id="50b3f-111">描述</span><span class="sxs-lookup"><span data-stu-id="50b3f-111">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="50b3f-112">要設定其 CorFlags 的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="50b3f-112">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="50b3f-113">選項</span><span class="sxs-lookup"><span data-stu-id="50b3f-113">Option</span></span>|<span data-ttu-id="50b3f-114">描述</span><span class="sxs-lookup"><span data-stu-id="50b3f-114">Description</span></span>|  
|:------------|-----------------|  
|`-32BIT[REQ]+`|<span data-ttu-id="50b3f-115">設定 32BITREQUIRED 旗標。</span><span class="sxs-lookup"><span data-stu-id="50b3f-115">Sets the 32BITREQUIRED flag.</span></span>|  
|`-32BIT[REQ]-`|<span data-ttu-id="50b3f-116">清除 32BITREQUIRED 旗標。</span><span class="sxs-lookup"><span data-stu-id="50b3f-116">Clears the 32BITREQUIRED flag.</span></span>|  
|`-32BITPREF+`|<span data-ttu-id="50b3f-117">設定 32BITPREFERRED 旗標。</span><span class="sxs-lookup"><span data-stu-id="50b3f-117">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="50b3f-118">應用程式在 64 位元平台上仍然以 32 位元處理序執行。</span><span class="sxs-lookup"><span data-stu-id="50b3f-118">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="50b3f-119">請只對 EXE 檔案設定這個旗標。</span><span class="sxs-lookup"><span data-stu-id="50b3f-119">Set this flag only on EXE files.</span></span> <span data-ttu-id="50b3f-120">如果在 DLL 上設定這個旗標，DLL 就無法在 64 位元處理序中載入，如此就會擲回 <xref:System.BadImageFormatException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="50b3f-120">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="50b3f-121">具有這個旗標的 EXE 檔案可以載入至 64 位元處理序。</span><span class="sxs-lookup"><span data-stu-id="50b3f-121">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="50b3f-122">.NET Framework 4.5 中的新增功能。</span><span class="sxs-lookup"><span data-stu-id="50b3f-122">New in the .NET Framework 4.5.</span></span>|  
|`-32BITPREF-`|<span data-ttu-id="50b3f-123">清除 32BITPREFERRED 旗標。</span><span class="sxs-lookup"><span data-stu-id="50b3f-123">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="50b3f-124">.NET Framework 4.5 中的新增功能。</span><span class="sxs-lookup"><span data-stu-id="50b3f-124">New in the .NET Framework 4.5.</span></span>|  
|`-?`|<span data-ttu-id="50b3f-125">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="50b3f-125">Displays command syntax and options for the tool.</span></span>|  
|`-Force`|<span data-ttu-id="50b3f-126">即使組件採用強式名稱，仍然強制進行更新。</span><span class="sxs-lookup"><span data-stu-id="50b3f-126">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="50b3f-127">**重要事項：** 如果您更新強式名稱組件，就必須先再次簽署該組件，再執行其程式碼。</span><span class="sxs-lookup"><span data-stu-id="50b3f-127">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|`-help`|<span data-ttu-id="50b3f-128">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="50b3f-128">Displays command syntax and options for the tool.</span></span>|  
|`-ILONLY+`|<span data-ttu-id="50b3f-129">設定 ILONLY 旗標。</span><span class="sxs-lookup"><span data-stu-id="50b3f-129">Sets the ILONLY flag.</span></span>|  
|`-ILONLY-`|<span data-ttu-id="50b3f-130">清除 ILONLY 旗標。</span><span class="sxs-lookup"><span data-stu-id="50b3f-130">Clears the ILONLY flag.</span></span>|  
|`-nologo`|<span data-ttu-id="50b3f-131">隱藏 Microsoft 程式啟始資訊顯示。</span><span class="sxs-lookup"><span data-stu-id="50b3f-131">Suppresses the Microsoft startup banner display.</span></span>|  
|`-RevertCLRHeader`|<span data-ttu-id="50b3f-132">將 CLR 標頭版本還原為 2.0。</span><span class="sxs-lookup"><span data-stu-id="50b3f-132">Reverts the CLR header version to 2.0.</span></span>|  
|`-UpgradeCLRHeader`|<span data-ttu-id="50b3f-133">將 CLR 標頭版本升級到 2.5。</span><span class="sxs-lookup"><span data-stu-id="50b3f-133">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="50b3f-134">**注意：** 組件的 CLR 標頭必須是 2.5 (含) 以上版本，才能以原本的形式執行。</span><span class="sxs-lookup"><span data-stu-id="50b3f-134">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50b3f-135">備註</span><span class="sxs-lookup"><span data-stu-id="50b3f-135">Remarks</span></span>  
 <span data-ttu-id="50b3f-136">如果未指定任何選項，則 CorFlags 轉換工具會針對所指定組件顯示旗標。</span><span class="sxs-lookup"><span data-stu-id="50b3f-136">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50b3f-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50b3f-137">See also</span></span>

- [<span data-ttu-id="50b3f-138">工具</span><span class="sxs-lookup"><span data-stu-id="50b3f-138">Tools</span></span>](index.md)
- [<span data-ttu-id="50b3f-139">64 位應用程式</span><span class="sxs-lookup"><span data-stu-id="50b3f-139">64-bit Applications</span></span>](../64-bit-apps.md)
- [<span data-ttu-id="50b3f-140">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="50b3f-140">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
