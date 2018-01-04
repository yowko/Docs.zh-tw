---
title: "ServiceModel 註冊工具 (ServiceModelReg.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 862c5635dd98933f57ec15ddcd20de043da69117
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="67c99-102">ServiceModel 註冊工具 (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="67c99-102">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="67c99-103">這個命令列工具可讓您在單一電腦上管理 WCF 及 WF 元件的註冊。</span><span class="sxs-lookup"><span data-stu-id="67c99-103">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="67c99-104">在一般情況下，您應該不需要使用這個工具，因為安裝時已對 WCF 及 WF 元件進行設定。</span><span class="sxs-lookup"><span data-stu-id="67c99-104">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="67c99-105">但如果您遇到服務啟用的問題，您可以嘗試使用這個工具來註冊元件。</span><span class="sxs-lookup"><span data-stu-id="67c99-105">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67c99-106">語法</span><span class="sxs-lookup"><span data-stu-id="67c99-106">Syntax</span></span>  
  
```  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="67c99-107">備註</span><span class="sxs-lookup"><span data-stu-id="67c99-107">Remarks</span></span>  
 <span data-ttu-id="67c99-108">您可以在下列位置找到這個工具：</span><span class="sxs-lookup"><span data-stu-id="67c99-108">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="67c99-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span><span class="sxs-lookup"><span data-stu-id="67c99-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67c99-110">ServiceModel 註冊工具上執行時[!INCLUDE[wv](../../../includes/wv-md.md)]、 **Windows 功能**對話方塊可能不會反映**Windows Communication Foundation HTTP 啟動**下的選項**Microsoft.NET Framework 3.0**已開啟。</span><span class="sxs-lookup"><span data-stu-id="67c99-110">When the ServiceModel Registration Tool is run on [!INCLUDE[wv](../../../includes/wv-md.md)], the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="67c99-111">**Windows 功能**對話方塊可以透過按一下**啟動**，然後按一下 **執行**然後輸入**OptionalFeatures**。</span><span class="sxs-lookup"><span data-stu-id="67c99-111">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="67c99-112">下表說明可與 ServiceModelReg.exe 搭配使用的選項。</span><span class="sxs-lookup"><span data-stu-id="67c99-112">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="67c99-113">選項</span><span class="sxs-lookup"><span data-stu-id="67c99-113">Option</span></span>|<span data-ttu-id="67c99-114">描述</span><span class="sxs-lookup"><span data-stu-id="67c99-114">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="67c99-115">安裝所有 WCF 和 WF 元件。</span><span class="sxs-lookup"><span data-stu-id="67c99-115">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="67c99-116">解除安裝所有 WCF 和 WF 元件。</span><span class="sxs-lookup"><span data-stu-id="67c99-116">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="67c99-117">修復所有 WCF 和 WF 元件。</span><span class="sxs-lookup"><span data-stu-id="67c99-117">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="67c99-118">安裝使用 –c 所指定的 WCF 和 WF 元件。</span><span class="sxs-lookup"><span data-stu-id="67c99-118">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="67c99-119">解除安裝使用 –c 所指定的 WCF 和 WF 元件。</span><span class="sxs-lookup"><span data-stu-id="67c99-119">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="67c99-120">安裝或解除安裝元件：</span><span class="sxs-lookup"><span data-stu-id="67c99-120">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="67c99-121">-httpnamespace-HTTP 命名空間保留</span><span class="sxs-lookup"><span data-stu-id="67c99-121">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="67c99-122">-tcpportsharing-TCP 連接埠共用服務</span><span class="sxs-lookup"><span data-stu-id="67c99-122">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="67c99-123">-tcpactivation – TCP 啟用服務 （不支援在.NET 4 用戶端設定檔）</span><span class="sxs-lookup"><span data-stu-id="67c99-123">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="67c99-124">-namedpipeactivation – 具名管道啟用服務 （不支援在.NET 4 用戶端設定檔</span><span class="sxs-lookup"><span data-stu-id="67c99-124">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="67c99-125">-msmqactivation – MSMQ 啟用服務 （不支援在.NET 4 用戶端設定檔</span><span class="sxs-lookup"><span data-stu-id="67c99-125">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="67c99-126">-etw-ETW 事件追蹤資訊清單 (Windows Vista 或更新版本)</span><span class="sxs-lookup"><span data-stu-id="67c99-126">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="67c99-127">無訊息模式 (僅顯示錯誤記錄)</span><span class="sxs-lookup"><span data-stu-id="67c99-127">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="67c99-128">詳細資訊模式。</span><span class="sxs-lookup"><span data-stu-id="67c99-128">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="67c99-129">不顯示版權和橫幅訊息。</span><span class="sxs-lookup"><span data-stu-id="67c99-129">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="67c99-130">顯示說明文字</span><span class="sxs-lookup"><span data-stu-id="67c99-130">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="67c99-131">修正 FileLoadException 錯誤</span><span class="sxs-lookup"><span data-stu-id="67c99-131">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="67c99-132">如果您的電腦上已安裝舊版的 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]，當您執行 ServiceModelReg 工具註冊新安裝時，可能會收到 `FileLoadFoundException` 錯誤。</span><span class="sxs-lookup"><span data-stu-id="67c99-132">If you installed previous versions of [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="67c99-133">即使您已手動移除舊安裝中的檔案，但 machine.config 設定仍保留原封不動，仍將發生這種情形。</span><span class="sxs-lookup"><span data-stu-id="67c99-133">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="67c99-134">得到的錯誤訊息與以下類似。</span><span class="sxs-lookup"><span data-stu-id="67c99-134">The error message is similar to the following.</span></span>  
  
```  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="67c99-135">您會在錯誤訊息中發現，先前發行的 Customer Technology Preview (CTP) 安裝了 System.ServiceModel Version 2.0.0.0 組件。</span><span class="sxs-lookup"><span data-stu-id="67c99-135">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="67c99-136">System.ServiceModel 組件目前的版本是 3.0.0.0。</span><span class="sxs-lookup"><span data-stu-id="67c99-136">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="67c99-137">因此，當您要在已安裝舊版 CTP [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 的電腦上安裝 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 的正式版時，便會遇到這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="67c99-137">Therefore, this issue is encountered when you want to install the official [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] release on a machine where an early CTP release of [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="67c99-138">ServiceModelReg.exe 無法清除舊版的項目，也無法註冊新版本項目。</span><span class="sxs-lookup"><span data-stu-id="67c99-138">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="67c99-139">唯一的解決方法就是手動編輯 machine.config。您可以在下列位置找到這個檔案。</span><span class="sxs-lookup"><span data-stu-id="67c99-139">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="67c99-140">如果您在 64 位元的電腦上執行 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]，可以在這個位置編輯相同的檔案。</span><span class="sxs-lookup"><span data-stu-id="67c99-140">If you are running [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="67c99-141">參考這個檔案中找到的任何 XML 節點"System.ServiceModel，Version = 2.0.0.0"，刪除這些節點及其任何子節點。</span><span class="sxs-lookup"><span data-stu-id="67c99-141">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="67c99-142">儲存檔案並重新執行 ServiceModelReg.exe，便可解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="67c99-142">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="67c99-143">範例</span><span class="sxs-lookup"><span data-stu-id="67c99-143">Examples</span></span>  
 <span data-ttu-id="67c99-144">下列範例顯示如何使用 ServiceModelReg.exe 工具的最常見選項。</span><span class="sxs-lookup"><span data-stu-id="67c99-144">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
```  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
