---
title: .NET Framework 工具
ms.date: 03/30/2017
helpviewer_keywords:
- command line, .NET Framework tools
- .NET Framework, tools
- tools [.NET Framework]
- running .NET Framework tools
ms.assetid: a2ca532d-91f7-426a-9303-417c2ee1247c
ms.openlocfilehash: 4503e2cff18f4aa901d20c76cfe4076a7fed3600
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715771"
---
# <a name="net-framework-tools"></a><span data-ttu-id="f8922-102">.NET Framework 工具</span><span class="sxs-lookup"><span data-stu-id="f8922-102">.NET Framework Tools</span></span>

<span data-ttu-id="f8922-103">.NET Framework 工具可讓您更輕鬆地建立、部署和管理以 .NET Framework 為目標的應用程式和元件。</span><span class="sxs-lookup"><span data-stu-id="f8922-103">The .NET Framework tools make it easier for you to create, deploy, and manage applications and components that target the .NET Framework.</span></span>

<span data-ttu-id="f8922-104">本節提及的大部分 .NET Framework 工具會隨 Visual Studio 自動安裝 </span><span class="sxs-lookup"><span data-stu-id="f8922-104">Most of the .NET Framework tools described in this section are automatically installed with Visual Studio.</span></span> <span data-ttu-id="f8922-105">若要下載 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)頁面。</span><span class="sxs-lookup"><span data-stu-id="f8922-105">To download Visual Studio, visit the [Visual Studio Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) page.</span></span>

<span data-ttu-id="f8922-106">除了組件快取檢視器 *（Shfusion.dll*） 之外，可以從命令列運行所有工具。</span><span class="sxs-lookup"><span data-stu-id="f8922-106">You can run all the tools from the command line with the exception of the Assembly Cache Viewer (*Shfusion.dll*).</span></span> <span data-ttu-id="f8922-107">您必須從檔資源管理器訪問*Shfusion.dll。*</span><span class="sxs-lookup"><span data-stu-id="f8922-107">You must access *Shfusion.dll* from File Explorer.</span></span>
  
<span data-ttu-id="f8922-108">執行命令列工具的最佳方式，是使用 Visual Studio 的 [開發人員命令提示字元]。</span><span class="sxs-lookup"><span data-stu-id="f8922-108">The best way to run the command-line tools is by using the Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="f8922-109">這些公用程式可讓您輕鬆執行工具，而不必巡覽至安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="f8922-109">These utilities enable you to run the tools easily, without navigating to the installation folder.</span></span> <span data-ttu-id="f8922-110">如需詳細資訊，請參閱[命令提示字元](developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="f8922-110">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f8922-111">某些工具為 32 位元電腦或 64 位元電腦專用。</span><span class="sxs-lookup"><span data-stu-id="f8922-111">Some tools are specific to either 32-bit computers or 64-bit computers.</span></span> <span data-ttu-id="f8922-112">請務必執行電腦適用的工具版本。</span><span class="sxs-lookup"><span data-stu-id="f8922-112">Be sure to run the appropriate version of the tool for your computer.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="f8922-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="f8922-113">In this section</span></span>

- [<span data-ttu-id="f8922-114">Al.exe (組件連結器)</span><span class="sxs-lookup"><span data-stu-id="f8922-114">Al.exe (Assembly Linker)</span></span>](al-exe-assembly-linker.md)  
<span data-ttu-id="f8922-115">從模組或資源檔中產生一個包含組件資訊清單的檔案。</span><span class="sxs-lookup"><span data-stu-id="f8922-115">Generates a file that has an assembly manifest from modules or resource files.</span></span>

- [<span data-ttu-id="f8922-116">Aximp.exe (Windows Forms ActiveX 控制項匯入工具)</span><span class="sxs-lookup"><span data-stu-id="f8922-116">Aximp.exe (Windows Forms ActiveX Control Importer)</span></span>](aximp-exe-windows-forms-activex-control-importer.md)  
<span data-ttu-id="f8922-117">將 COM 類型程式庫中的類型定義轉換為 Windows Form 控制項中的 ActiveX 控制項。</span><span class="sxs-lookup"><span data-stu-id="f8922-117">Converts type definitions in a COM type library for an ActiveX control into a Windows Forms control.</span></span>

- [<span data-ttu-id="f8922-118">Caspol.exe (程式碼存取安全性原則工具)</span><span class="sxs-lookup"><span data-stu-id="f8922-118">Caspol.exe (Code Access Security Policy Tool)</span></span>](caspol-exe-code-access-security-policy-tool.md)  
<span data-ttu-id="f8922-119">可讓您檢視和設定電腦原則層級、使用者原則層級和企業原則層級的安全性原則。</span><span class="sxs-lookup"><span data-stu-id="f8922-119">Enables you to view and configure security policy for the machine policy level, the user policy level, and the enterprise policy level.</span></span> <span data-ttu-id="f8922-120">在 .NET 框架 4 及更高版本中，此工具不會影響代碼訪問安全 （CAS） 策略，`true`[\<除非舊 CasPolicy> 元素](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)設置為 。</span><span class="sxs-lookup"><span data-stu-id="f8922-120">In the .NET Framework 4 and later, this tool does not affect code access security (CAS) policy unless the [\<legacyCasPolicy> element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) is set to `true`.</span></span> <span data-ttu-id="f8922-121">如需詳細資訊，請參閱[安全性變更](../security/security-changes.md)。</span><span class="sxs-lookup"><span data-stu-id="f8922-121">For more information, see [Security Changes](../security/security-changes.md).</span></span>

- [<span data-ttu-id="f8922-122">Cert2spc.exe (軟體發行者憑證測試工具)</span><span class="sxs-lookup"><span data-stu-id="f8922-122">Cert2spc.exe (Software Publisher Certificate Test Tool)</span></span>](cert2spc-exe-software-publisher-certificate-test-tool.md)  
<span data-ttu-id="f8922-123">從一個或多個 X.509 憑證建立軟體發行者憑證 (SPC)。</span><span class="sxs-lookup"><span data-stu-id="f8922-123">Creates a Software Publisher's Certificate (SPC) from one or more X.509 certificates.</span></span> <span data-ttu-id="f8922-124">這個工具僅供測試用。</span><span class="sxs-lookup"><span data-stu-id="f8922-124">This tool is for testing purposes only.</span></span>

- [<span data-ttu-id="f8922-125">Certmgr.exe (憑證管理員工具)</span><span class="sxs-lookup"><span data-stu-id="f8922-125">Certmgr.exe (Certificate Manager Tool)</span></span>](certmgr-exe-certificate-manager-tool.md)  
<span data-ttu-id="f8922-126">管理憑證、憑證信任清單 (CTL) 和憑證廢止清單 (CRL)。</span><span class="sxs-lookup"><span data-stu-id="f8922-126">Manages certificates, certificate trust lists (CTLs), and certificate revocation lists (CRLs).</span></span>

- [<span data-ttu-id="f8922-127">Clrver.exe (CLR 版本工具)</span><span class="sxs-lookup"><span data-stu-id="f8922-127">Clrver.exe (CLR Version Tool)</span></span>](clrver-exe-clr-version-tool.md)  
<span data-ttu-id="f8922-128">報告電腦上通用語言運行時 （CLR） 的所有已安裝版本。</span><span class="sxs-lookup"><span data-stu-id="f8922-128">Reports all the installed versions of the common language runtime (CLR) on the computer.</span></span>

- [<span data-ttu-id="f8922-129">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="f8922-129">Command Prompts</span></span>](developer-command-prompt-for-vs.md)  
<span data-ttu-id="f8922-130">使您能夠更輕鬆地使用 .NET 框架工具。</span><span class="sxs-lookup"><span data-stu-id="f8922-130">Enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="f8922-131">它是命令提示字元，可自動設定特定的環境變數。</span><span class="sxs-lookup"><span data-stu-id="f8922-131">It is a command prompt that automatically sets specific environment variables.</span></span>

- [<span data-ttu-id="f8922-132">CorFlags.exe (CorFlags 轉換工具)</span><span class="sxs-lookup"><span data-stu-id="f8922-132">CorFlags.exe (CorFlags Conversion Tool)</span></span>](corflags-exe-corflags-conversion-tool.md)  
<span data-ttu-id="f8922-133">可讓您設定可攜式執行檔 (PE) 影像之標頭的 CorFlags 區段。</span><span class="sxs-lookup"><span data-stu-id="f8922-133">Lets you configure the CorFlags section of the header of a portable executable (PE) image.</span></span>

- [<span data-ttu-id="f8922-134">Fuslogvw.exe (組件繫結記錄檔檢視器)</span><span class="sxs-lookup"><span data-stu-id="f8922-134">Fuslogvw.exe (Assembly Binding Log Viewer)</span></span>](fuslogvw-exe-assembly-binding-log-viewer.md)  
<span data-ttu-id="f8922-135">顯示有關組件繫結的資訊，可以協助您診斷 .NET Framework 為何不能在執行階段時找到組件。</span><span class="sxs-lookup"><span data-stu-id="f8922-135">Displays information about assembly binds to help you diagnose why the .NET Framework cannot locate an assembly at run time.</span></span>

- [<span data-ttu-id="f8922-136">Gacutil.exe（全球裝配緩存工具）</span><span class="sxs-lookup"><span data-stu-id="f8922-136">Gacutil.exe (Global Assembly Cache Tool)</span></span>](gacutil-exe-gac-tool.md)  
<span data-ttu-id="f8922-137">可讓您檢視和操作全域組件快取的內容並下載快取。</span><span class="sxs-lookup"><span data-stu-id="f8922-137">Lets you view and manipulate the contents of the global assembly cache and download cache.</span></span>

- [<span data-ttu-id="f8922-138">Ilasm.exe (IL 組譯工具)</span><span class="sxs-lookup"><span data-stu-id="f8922-138">Ilasm.exe (IL Assembler)</span></span>](ilasm-exe-il-assembler.md)  
<span data-ttu-id="f8922-139">從中繼語言 (IL) 中產生可攜式執行檔 (PE)。</span><span class="sxs-lookup"><span data-stu-id="f8922-139">Generates a portable executable (PE) file from intermediate language (IL).</span></span> <span data-ttu-id="f8922-140">您可以執行產生的可執行檔，來判斷 IL 是否如預期般地執行。</span><span class="sxs-lookup"><span data-stu-id="f8922-140">You can run the resulting executable to determine whether the IL performs as expected.</span></span>

- [<span data-ttu-id="f8922-141">Ildasm.exe (IL 反組譯工具)</span><span class="sxs-lookup"><span data-stu-id="f8922-141">Ildasm.exe (IL Disassembler)</span></span>](ildasm-exe-il-disassembler.md)  
<span data-ttu-id="f8922-142">使用包含中繼語言 (IL) 程式碼的可攜式執行檔 (PE)，並建立可以輸入至 IL 組譯工具 (Ilasm.exe) 的文字檔。</span><span class="sxs-lookup"><span data-stu-id="f8922-142">Takes a portable executable (PE) file that contains intermediate language (IL) code and creates a text file that can be input to the IL Assembler (Ilasm.exe).</span></span>

- [<span data-ttu-id="f8922-143">Installutil.exe (安裝程式工具)</span><span class="sxs-lookup"><span data-stu-id="f8922-143">Installutil.exe (Installer Tool)</span></span>](installutil-exe-installer-tool.md)  
<span data-ttu-id="f8922-144">可讓您藉由執行所指定組件的 Installer 元件，來安裝和解除安裝伺服器資源 </span><span class="sxs-lookup"><span data-stu-id="f8922-144">Enables you to install and uninstall server resources by executing the installer components in a specified assembly.</span></span> <span data-ttu-id="f8922-145">(使用 <xref:System.Configuration.Install> 命名空間中的類別)。</span><span class="sxs-lookup"><span data-stu-id="f8922-145">(Works with classes in the <xref:System.Configuration.Install> namespace.)</span></span>

- [<span data-ttu-id="f8922-146">Lc.exe (授權編譯器)</span><span class="sxs-lookup"><span data-stu-id="f8922-146">Lc.exe (License Compiler)</span></span>](lc-exe-license-compiler.md)  
<span data-ttu-id="f8922-147">讀取包含許可資訊的文字檔，並生成可以嵌入作為資源的常見語言運行時可*執行檔的文本*檔。</span><span class="sxs-lookup"><span data-stu-id="f8922-147">Reads text files that contain licensing information and produces a *.licenses* file that can be embedded in a common language runtime executable as a resource.</span></span>

- [<span data-ttu-id="f8922-148">Mage.exe (資訊清單產生和編輯工具)</span><span class="sxs-lookup"><span data-stu-id="f8922-148">Mage.exe (Manifest Generation and Editing Tool)</span></span>](mage-exe-manifest-generation-and-editing-tool.md)  
<span data-ttu-id="f8922-149">可讓您建立、編輯和簽署應用程式以及部署資訊清單。</span><span class="sxs-lookup"><span data-stu-id="f8922-149">Lets you create, edit, and sign application and deployment manifests.</span></span> <span data-ttu-id="f8922-150">由於 *Mage.exe* 是命令列工具，因此可以從批次指令碼及其他 Windows 應用程式 (包括 ASP.NET 應用程式) 中執行。</span><span class="sxs-lookup"><span data-stu-id="f8922-150">As a command-line tool, *Mage.exe* can be run from both batch scripts and other Windows-based applications, including ASP.NET applications.</span></span>

- [<span data-ttu-id="f8922-151">MageUI.exe (資訊清單產生和編輯工具，圖形化用戶端)</span><span class="sxs-lookup"><span data-stu-id="f8922-151">MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)</span></span>](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)  
<span data-ttu-id="f8922-152">支援與命令列工具 Mage.exe 相同的功能，但使用 Windows 架構使用者介面 (UI)。</span><span class="sxs-lookup"><span data-stu-id="f8922-152">Supports the same functionality as the command-line tool Mage.exe, but uses a Windows-based user interface (UI).</span></span> <span data-ttu-id="f8922-153">支援與命令列工具*Mage.exe*相同的功能，但使用基於 Windows 的使用者介面 （UI）。</span><span class="sxs-lookup"><span data-stu-id="f8922-153">Supports the same functionality as the command-line tool *Mage.exe*, but uses a Windows-based user interface (UI).</span></span>

- [<span data-ttu-id="f8922-154">MDbg.exe (.NET Framework 命令列偵錯工具)</span><span class="sxs-lookup"><span data-stu-id="f8922-154">MDbg.exe (.NET Framework Command-Line Debugger)</span></span>](mdbg-exe.md)  
<span data-ttu-id="f8922-155">協助工具廠商和應用程式開發人員尋找並修復以 .NET Framework 通用語言執行平台為目標的程式中的 Bug。</span><span class="sxs-lookup"><span data-stu-id="f8922-155">Helps tools vendors and application developers find and fix bugs in programs that target the .NET Framework common language runtime.</span></span> <span data-ttu-id="f8922-156">這個工具使用執行階段偵錯 API 來提供偵錯服務。</span><span class="sxs-lookup"><span data-stu-id="f8922-156">This tool uses the runtime debugging API to provide debugging services.</span></span>

- [<span data-ttu-id="f8922-157">Mgmtclassgen.exe (管理強類型類別產生器)</span><span class="sxs-lookup"><span data-stu-id="f8922-157">Mgmtclassgen.exe (Management Strongly Typed Class Generator)</span></span>](mgmtclassgen-exe.md)  
<span data-ttu-id="f8922-158">可讓您為指定的 Windows Management Instrumentation (WMI) 類別，產生早期繫結 Managed 類別。</span><span class="sxs-lookup"><span data-stu-id="f8922-158">Enables you to generate an early-bound managed class for a specified Windows Management Instrumentation (WMI) class.</span></span>

- [<span data-ttu-id="f8922-159">Mpgo.exe (Managed 特性指引最佳化工具)</span><span class="sxs-lookup"><span data-stu-id="f8922-159">Mpgo.exe (Managed Profile Guided Optimization Tool)</span></span>](mpgo-exe-managed-profile-guided-optimization-tool.md)  
<span data-ttu-id="f8922-160">可讓您調整使用一般使用者情節的原生映像組件。</span><span class="sxs-lookup"><span data-stu-id="f8922-160">Enables you to tune native image assemblies using common end-user scenarios.</span></span> <span data-ttu-id="f8922-161">Mpgo.exe 可讓您使用應用程式開發人員選出的訓練情節，產生和使用原生映像應用程式組件 (不是 .NET Framework 組件) 的分析資料。</span><span class="sxs-lookup"><span data-stu-id="f8922-161">Mpgo.exe allows the generation and consumption of profile data for native image application assemblies (not the .NET Framework assemblies) using training scenarios selected by the application developer.</span></span>

- [<span data-ttu-id="f8922-162">Ngen.exe (原生映像產生器)</span><span class="sxs-lookup"><span data-stu-id="f8922-162">Ngen.exe (Native Image Generator)</span></span>](ngen-exe-native-image-generator.md)  
<span data-ttu-id="f8922-163">透過使用原生影像 (含有已編譯之處理器特定機器碼的檔案)，改善 Managed 應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="f8922-163">Improves the performance of managed applications through the use of native images (files containing compiled processor-specific machine code).</span></span> <span data-ttu-id="f8922-164">執行階段就可以從快取中使用原生映像，而不是使用 Just-In-Time (JIT) 編譯器來編譯原始組件。</span><span class="sxs-lookup"><span data-stu-id="f8922-164">The runtime can use native images from the cache instead of using the just-in-time (JIT) compiler to compile the original assembly.</span></span>

- [<span data-ttu-id="f8922-165">Peverify.exe (PEVerify 工具)</span><span class="sxs-lookup"><span data-stu-id="f8922-165">Peverify.exe (PEVerify Tool)</span></span>](peverify-exe-peverify-tool.md)  
<span data-ttu-id="f8922-166">可以協助您驗證 Microsoft Intermediate Language (MSIL) 程式碼及相關的中繼資料是否符合類型安全需求。</span><span class="sxs-lookup"><span data-stu-id="f8922-166">Helps you verify whether your Microsoft intermediate language (MSIL) code and associated metadata meet type safety requirements.</span></span>

- [<span data-ttu-id="f8922-167">Regasm.exe (組件登錄工具)</span><span class="sxs-lookup"><span data-stu-id="f8922-167">Regasm.exe (Assembly Registration Tool)</span></span>](regasm-exe-assembly-registration-tool.md)  
<span data-ttu-id="f8922-168">讀取組件內的中繼資料，並將需要的項目加入登錄。</span><span class="sxs-lookup"><span data-stu-id="f8922-168">Reads the metadata within an assembly and adds the necessary entries to the registry.</span></span> <span data-ttu-id="f8922-169">這可讓 COM 用戶端顯示為 .NET Framework 類別。</span><span class="sxs-lookup"><span data-stu-id="f8922-169">This enables COM clients to appear as .NET Framework classes.</span></span>

- [<span data-ttu-id="f8922-170">Regsvcs.exe (.NET 服務安裝工具)</span><span class="sxs-lookup"><span data-stu-id="f8922-170">Regsvcs.exe (.NET Services Installation Tool)</span></span>](regsvcs-exe-net-services-installation-tool.md)  
<span data-ttu-id="f8922-171">載入並註冊組件、產生並安裝類型程式庫至指定的 COM+ 1.0 版應用程式，以及設定您已利用程式設計方式加入至類別的服務。</span><span class="sxs-lookup"><span data-stu-id="f8922-171">Loads and registers an assembly, generates and installs a type library into a specified COM+ version 1.0 application, and configures services that you have added programmatically to a class.</span></span>

- [<span data-ttu-id="f8922-172">Resgen.exe (資源檔產生器)</span><span class="sxs-lookup"><span data-stu-id="f8922-172">Resgen.exe (Resource File Generator)</span></span>](resgen-exe-resource-file-generator.md)  
<span data-ttu-id="f8922-173">將文本 *（.txt*或 *.restext）* 檔和基於 XML 的資源格式 *（.resx*） 檔轉換為可嵌入到運行時二進位可執行檔或編譯到附屬程式集中的通用語言運行時二進位檔案 *（.resource）* 檔。</span><span class="sxs-lookup"><span data-stu-id="f8922-173">Converts text (*.txt* or *.restext*) files and XML-based resource format (*.resx*) files to common language runtime binary (*.resources*) files that can be embedded in a runtime binary executable or compiled into satellite assemblies.</span></span>

- [<span data-ttu-id="f8922-174">SecAnnotate.exe (.NET Security Annotator 工具)</span><span class="sxs-lookup"><span data-stu-id="f8922-174">SecAnnotate.exe (.NET Security Annotator Tool)</span></span>](secannotate-exe-net-security-annotator-tool.md)  
<span data-ttu-id="f8922-175">識別組件的 `SecurityCritical` 和 `SecuritySafeCritical` 的部分。</span><span class="sxs-lookup"><span data-stu-id="f8922-175">Identifies the `SecurityCritical` and `SecuritySafeCritical` portions of an assembly.</span></span>

- [<span data-ttu-id="f8922-176">SignTool.exe (簽署工具)</span><span class="sxs-lookup"><span data-stu-id="f8922-176">SignTool.exe (Sign Tool)</span></span>](signtool-exe.md)  
<span data-ttu-id="f8922-177">數位簽署檔案、驗證檔案中的簽章，以及為檔案加上時間戳記。</span><span class="sxs-lookup"><span data-stu-id="f8922-177">Digitally signs files, verifies signatures in files, and time-stamps files.</span></span>

- [<span data-ttu-id="f8922-178">Sn.exe (強式名稱工具)</span><span class="sxs-lookup"><span data-stu-id="f8922-178">Sn.exe (Strong Name Tool)</span></span>](sn-exe-strong-name-tool.md)  
<span data-ttu-id="f8922-179">幫助以強式名稱 (Strong Name) 建立組件。</span><span class="sxs-lookup"><span data-stu-id="f8922-179">Helps create assemblies with strong names.</span></span> <span data-ttu-id="f8922-180">這個工具提供了金鑰管理、簽章產生和簽章驗證的選項。</span><span class="sxs-lookup"><span data-stu-id="f8922-180">This tool provides options for key management, signature generation, and signature verification.</span></span>

- [<span data-ttu-id="f8922-181">SOS.dll (SOS 偵錯擴充功能)</span><span class="sxs-lookup"><span data-stu-id="f8922-181">SOS.dll (SOS Debugging Extension)</span></span>](sos-dll-sos-debugging-extension.md)  
<span data-ttu-id="f8922-182">提供內部通用語言執行平台環境的相關資訊，以協助您在 WinDbg.exe 偵錯工具和 Visual Studio 中偵錯 Managed 程式。</span><span class="sxs-lookup"><span data-stu-id="f8922-182">Helps you debug managed programs in the WinDbg.exe debugger and in Visual Studio by providing information about the internal common language runtime environment.</span></span>

- [<span data-ttu-id="f8922-183">SqlMetal.exe (程式碼產生工具)</span><span class="sxs-lookup"><span data-stu-id="f8922-183">SqlMetal.exe (Code Generation Tool)</span></span>](sqlmetal-exe-code-generation-tool.md)  
<span data-ttu-id="f8922-184">為 .NET Framework 的 LINQ to SQL 元件產生程式碼和對應。</span><span class="sxs-lookup"><span data-stu-id="f8922-184">Generates code and mapping for the LINQ to SQL component of the .NET Framework.</span></span>

- [<span data-ttu-id="f8922-185">Storeadm.exe (隔離儲存區工具)</span><span class="sxs-lookup"><span data-stu-id="f8922-185">Storeadm.exe (Isolated Storage Tool)</span></span>](storeadm-exe-isolated-storage-tool.md)  
<span data-ttu-id="f8922-186">管理隔離儲存區 (Isolated Storage)，提供選項以列出使用者的存放區並加以刪除。</span><span class="sxs-lookup"><span data-stu-id="f8922-186">Manages isolated storage; provides options for listing the user's stores and deleting them.</span></span>

- [<span data-ttu-id="f8922-187">Tlbexp.exe (類型程式庫匯出工具)</span><span class="sxs-lookup"><span data-stu-id="f8922-187">Tlbexp.exe (Type Library Exporter)</span></span>](tlbexp-exe-type-library-exporter.md)  
<span data-ttu-id="f8922-188">產生類型程式庫，類型程式庫會描述通用語言執行平台 (CLR) 組件中所定義的類型。</span><span class="sxs-lookup"><span data-stu-id="f8922-188">Generates a type library that describes the types that are defined in a common language runtime assembly.</span></span>

- [<span data-ttu-id="f8922-189">Tlbimp.exe (類型程式庫匯入工具)</span><span class="sxs-lookup"><span data-stu-id="f8922-189">Tlbimp.exe (Type Library Importer)</span></span>](tlbimp-exe-type-library-importer.md)  
<span data-ttu-id="f8922-190">將 COM 類型程式庫中找到的類型定義轉換為通用語言執行平台組件中的等效定義。</span><span class="sxs-lookup"><span data-stu-id="f8922-190">Converts the type definitions found in a COM type library into equivalent definitions in a common language runtime assembly.</span></span>

- [<span data-ttu-id="f8922-191">Winmdexp.exe (Windows 執行階段中繼資料匯出工具)</span><span class="sxs-lookup"><span data-stu-id="f8922-191">Winmdexp.exe (Windows Runtime Metadata Export Tool)</span></span>](winmdexp-exe-windows-runtime-metadata-export-tool.md)  
<span data-ttu-id="f8922-192">將編譯為 *.winmdobj*檔的 .NET Framework 程式集匯出到 Windows 運行時元件中，該元件打包為包含 Windows 運行時中繼資料和實現資訊的 *.winmd*檔。</span><span class="sxs-lookup"><span data-stu-id="f8922-192">Exports a .NET Framework assembly that is compiled as a *.winmdobj* file into a Windows Runtime component, which is packaged as a *.winmd* file that contains both Windows Runtime metadata and implementation information.</span></span>

- [<span data-ttu-id="f8922-193">Winres.exe (Windows Forms 資源編輯器)</span><span class="sxs-lookup"><span data-stu-id="f8922-193">Winres.exe (Windows Forms Resource Editor)</span></span>](winres-exe-windows-forms-resource-editor.md)  
<span data-ttu-id="f8922-194">説明您當地語系化 Windows 表單使用的使用者介面 *（UI） 資源（.resx*或 *.resource*檔）。</span><span class="sxs-lookup"><span data-stu-id="f8922-194">Helps you localize user interface (UI) resources (*.resx* or *.resources* files) that are used by Windows Forms.</span></span> <span data-ttu-id="f8922-195">您可以解譯字串，然後調整大小、移動和隱藏控制項來容納當地語系化的字串。</span><span class="sxs-lookup"><span data-stu-id="f8922-195">You can translate strings, and then size, move, and hide controls to accommodate the localized strings.</span></span>

## <a name="related-sections"></a><span data-ttu-id="f8922-196">相關章節</span><span class="sxs-lookup"><span data-stu-id="f8922-196">Related sections</span></span>

- <span data-ttu-id="f8922-197">[WPF 工具](https://docs.microsoft.com/previous-versions/ms742404(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="f8922-197">[WPF Tools](https://docs.microsoft.com/previous-versions/ms742404(v=vs.110))</span></span>  
<span data-ttu-id="f8922-198">包括 isXPS Conformance 工具 (isXPS.exe) 和效能程式碼剖析工具這類工具。</span><span class="sxs-lookup"><span data-stu-id="f8922-198">Includes tools such as the isXPS Conformance tool (isXPS.exe) and performance profiling tools.</span></span>

- [<span data-ttu-id="f8922-199">Windows Communication Foundation 工具</span><span class="sxs-lookup"><span data-stu-id="f8922-199">Windows Communication Foundation Tools</span></span>](../wcf/tools.md)  
<span data-ttu-id="f8922-200">包含多種工具，可以幫助您更輕鬆地建立、部署及管理 Windows Communication Foundation (WCF) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f8922-200">Includes tools that make it easier for you to create, deploy, and manage Windows Communication Foundation (WCF) applications.</span></span>
