---
title: ServiceModel 註冊工具 (ServiceModelReg.exe)
description: 如果您在服務啟用方面遇到問題，請使用此命令列工具來管理單一電腦上的 WCF 和 WF 元件註冊。
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: 347b1b8071abe7d8eb7e16ffd879c1fdb9825bc7
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245891"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="65109-103">ServiceModel 註冊工具 (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="65109-103">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="65109-104">這個命令列工具可讓您在單一電腦上管理 WCF 及 WF 元件的註冊。</span><span class="sxs-lookup"><span data-stu-id="65109-104">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="65109-105">在一般情況下，您應該不需要使用這個工具，因為安裝時已對 WCF 及 WF 元件進行設定。</span><span class="sxs-lookup"><span data-stu-id="65109-105">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="65109-106">但如果您遇到服務啟用的問題，您可以嘗試使用這個工具來註冊元件。</span><span class="sxs-lookup"><span data-stu-id="65109-106">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65109-107">語法</span><span class="sxs-lookup"><span data-stu-id="65109-107">Syntax</span></span>  
  
```console  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="65109-108">備註</span><span class="sxs-lookup"><span data-stu-id="65109-108">Remarks</span></span>  
 <span data-ttu-id="65109-109">您可以在下列位置找到這個工具：</span><span class="sxs-lookup"><span data-stu-id="65109-109">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="65109-110">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="65109-110">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
> [!NOTE]
> <span data-ttu-id="65109-111">當 System.servicemodel 註冊工具在 Windows Vista 上執行時，[ **Windows 功能**] 對話方塊可能不會反映 [ **Microsoft .NET Framework 3.0** ] 底下的 [ **Windows Communication Foundation HTTP**啟動] 選項已開啟。</span><span class="sxs-lookup"><span data-stu-id="65109-111">When the ServiceModel Registration Tool is run on Windows Vista, the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="65109-112">按一下 [**開始**]，然後按一下 [**執行**]，再輸入**OptionalFeatures**，即可存取 [ **Windows 功能**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="65109-112">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="65109-113">下表說明可與 ServiceModelReg.exe 搭配使用的選項。</span><span class="sxs-lookup"><span data-stu-id="65109-113">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="65109-114">選項</span><span class="sxs-lookup"><span data-stu-id="65109-114">Option</span></span>|<span data-ttu-id="65109-115">描述</span><span class="sxs-lookup"><span data-stu-id="65109-115">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="65109-116">安裝所有 WCF 和 WF 元件。</span><span class="sxs-lookup"><span data-stu-id="65109-116">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="65109-117">解除安裝所有 WCF 和 WF 元件。</span><span class="sxs-lookup"><span data-stu-id="65109-117">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="65109-118">修復所有 WCF 和 WF 元件。</span><span class="sxs-lookup"><span data-stu-id="65109-118">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="65109-119">安裝使用 –c 所指定的 WCF 和 WF 元件。</span><span class="sxs-lookup"><span data-stu-id="65109-119">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="65109-120">解除安裝使用 –c 所指定的 WCF 和 WF 元件。</span><span class="sxs-lookup"><span data-stu-id="65109-120">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="65109-121">安裝或解除安裝元件：</span><span class="sxs-lookup"><span data-stu-id="65109-121">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="65109-122">-HTTPnamespace – HTTP 命名空間保留</span><span class="sxs-lookup"><span data-stu-id="65109-122">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="65109-123">-tcpportsharing – TCP 埠共用服務</span><span class="sxs-lookup"><span data-stu-id="65109-123">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="65109-124">-tcpactivation – TCP 啟用服務（在 .NET 4 用戶端設定檔上不支援）</span><span class="sxs-lookup"><span data-stu-id="65109-124">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="65109-125">-nameDPIpeactivation –具名管道啟用服務（在 .NET 4 用戶端設定檔上不支援</span><span class="sxs-lookup"><span data-stu-id="65109-125">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="65109-126">-msmqactivation – MSMQ 啟用服務（在 .NET 4 用戶端設定檔上不支援</span><span class="sxs-lookup"><span data-stu-id="65109-126">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="65109-127">-etw – ETW 事件追蹤資訊清單（Windows Vista 或更新版本）</span><span class="sxs-lookup"><span data-stu-id="65109-127">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="65109-128">無訊息模式 (僅顯示錯誤記錄)</span><span class="sxs-lookup"><span data-stu-id="65109-128">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="65109-129">詳細資訊模式。</span><span class="sxs-lookup"><span data-stu-id="65109-129">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="65109-130">不顯示版權和橫幅訊息。</span><span class="sxs-lookup"><span data-stu-id="65109-130">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="65109-131">顯示說明文字</span><span class="sxs-lookup"><span data-stu-id="65109-131">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="65109-132">修正 FileLoadException 錯誤</span><span class="sxs-lookup"><span data-stu-id="65109-132">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="65109-133">如果您在電腦上安裝了舊版的 WCF， `FileLoadFoundException` 當您執行 servicemodelreg.exe 工具註冊新安裝時，可能會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="65109-133">If you installed previous versions of WCF on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="65109-134">即使您已手動移除舊安裝中的檔案，但 machine.config 設定仍保留原封不動，仍將發生這種情形。</span><span class="sxs-lookup"><span data-stu-id="65109-134">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="65109-135">得到的錯誤訊息與以下類似。</span><span class="sxs-lookup"><span data-stu-id="65109-135">The error message is similar to the following.</span></span>  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="65109-136">您會在錯誤訊息中發現，先前發行的 Customer Technology Preview (CTP) 安裝了 System.ServiceModel Version 2.0.0.0 組件。</span><span class="sxs-lookup"><span data-stu-id="65109-136">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="65109-137">System.ServiceModel 組件目前的版本是 3.0.0.0。</span><span class="sxs-lookup"><span data-stu-id="65109-137">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="65109-138">因此，當您想要在已安裝 WCF 的早期 CTP 版本但未完全卸載的電腦上安裝官方 WCF 版本時，就會發生此問題。</span><span class="sxs-lookup"><span data-stu-id="65109-138">Therefore, this issue is encountered when you want to install the official WCF release on a machine where an early CTP release of WCF was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="65109-139">ServiceModelReg.exe 無法清除舊版的項目，也無法註冊新版本項目。</span><span class="sxs-lookup"><span data-stu-id="65109-139">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="65109-140">唯一的解決方法就是手動編輯 machine.config。您可以在下列位置找到這個檔案。</span><span class="sxs-lookup"><span data-stu-id="65109-140">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="65109-141">如果您是在64位的電腦上執行 WCF，您也應該在此位置編輯相同的檔案。</span><span class="sxs-lookup"><span data-stu-id="65109-141">If you are running WCF on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="65109-142">找出此檔案中參考 "System.servicemodel，Version = 2.0.0.0" 的任何 XML 節點，並刪除它們和任何子節點。</span><span class="sxs-lookup"><span data-stu-id="65109-142">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="65109-143">儲存檔案並重新執行 ServiceModelReg.exe，便可解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="65109-143">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="65109-144">範例</span><span class="sxs-lookup"><span data-stu-id="65109-144">Examples</span></span>  
 <span data-ttu-id="65109-145">下列範例顯示如何使用 ServiceModelReg.exe 工具的最常見選項。</span><span class="sxs-lookup"><span data-stu-id="65109-145">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
```console  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
