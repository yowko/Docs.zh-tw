---
title: Certmgr.exe (憑證管理員工具)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates, managing
- CRLs
- certificate trust lists
- Certmgr.exe
- Certificate Manager tool
- CTLs
- certificate revocation lists
ms.assetid: 7e953b43-1374-4bbc-814f-53ca1b6b52bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a4cb3f126a51d6bf7027edb88b8fec74c6785d2
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44178204"
---
# <a name="certmgrexe-certificate-manager-tool"></a><span data-ttu-id="a182d-102">Certmgr.exe (憑證管理員工具)</span><span class="sxs-lookup"><span data-stu-id="a182d-102">Certmgr.exe (Certificate Manager Tool)</span></span>
<span data-ttu-id="a182d-103">憑證管理員工具 (Certmgr.exe) 可以管理憑證、憑證信任清單 (CTL) 和憑證撤銷清單 (CRL)。</span><span class="sxs-lookup"><span data-stu-id="a182d-103">The Certificate Manager tool (Certmgr.exe) manages certificates, certificate trust lists (CTLs), and certificate revocation lists (CRLs).</span></span>  
  
 <span data-ttu-id="a182d-104">憑證管理員會隨 Visual Studio 自動安裝。</span><span class="sxs-lookup"><span data-stu-id="a182d-104">The Certificate Manager is automatically installed with Visual Studio.</span></span> <span data-ttu-id="a182d-105">若要啟動工具，請使用[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="a182d-105">To start the tool, use the [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a182d-106">憑證管理工具 (Certmgr.exe) 是一個命令列公用程式，而憑證 (Certmgr.msc) 則是 Microsoft Management Console (MMC) 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="a182d-106">The Certificate Manager tool (Certmgr.exe) is a command-line utility, whereas Certificates (Certmgr.msc) is a Microsoft Management Console (MMC) snap-in.</span></span> <span data-ttu-id="a182d-107">因為 Certmgr.msc 通常會位於 Windows 系統目錄中，在命令列中輸入 `certmgr` 可能會載入憑證 MMC 嵌入管理單元，即使您已開啟 Visual Studio 命令提示符號也一樣。</span><span class="sxs-lookup"><span data-stu-id="a182d-107">Because Certmgr.msc is usually found in the Windows System directory, entering `certmgr` at the command line may load the Certificates MMC snap-in even if you have opened the Visual Studio Command Prompt.</span></span> <span data-ttu-id="a182d-108">發生這種情況是因為嵌入式管理單元的路徑在 PATH 環境變數中位於憑證管理員工具的路徑之前。</span><span class="sxs-lookup"><span data-stu-id="a182d-108">This occurs because the path to the snap-in precedes the path to the Certificate Manager tool in the PATH environment variable.</span></span> <span data-ttu-id="a182d-109">如果您遇到此問題，可以透過指定可執行檔的路徑來執行 Certmgr.exe 指令。</span><span class="sxs-lookup"><span data-stu-id="a182d-109">If you encounter this problem, you can execute Certmgr.exe commands by specifying the path to the executable.</span></span>  
  
 <span data-ttu-id="a182d-110">此工具會自動與 Visual Studio 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="a182d-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="a182d-111">若要執行此工具，請使用 [開發人員命令提示字元] \(或 Windows 7 中的 [Visual Studio 命令提示字元])。</span><span class="sxs-lookup"><span data-stu-id="a182d-111">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="a182d-112">如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="a182d-112">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="a182d-113">如需 X.509 憑證的概觀，請參閱[使用憑證](../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="a182d-113">For an overview of X.509 certificates, see [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
 <span data-ttu-id="a182d-114">在命令提示字元下輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="a182d-114">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a182d-115">語法</span><span class="sxs-lookup"><span data-stu-id="a182d-115">Syntax</span></span>  
  
```  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a182d-116">參數</span><span class="sxs-lookup"><span data-stu-id="a182d-116">Parameters</span></span>  
  
|<span data-ttu-id="a182d-117">引數</span><span class="sxs-lookup"><span data-stu-id="a182d-117">Argument</span></span>|<span data-ttu-id="a182d-118">描述</span><span class="sxs-lookup"><span data-stu-id="a182d-118">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="a182d-119">*sourceStorename*</span><span class="sxs-lookup"><span data-stu-id="a182d-119">*sourceStorename*</span></span>|<span data-ttu-id="a182d-120">憑證存放區，包含現有的憑證、CTL，或是要新增、刪除、儲存或顯示的 CRL。</span><span class="sxs-lookup"><span data-stu-id="a182d-120">The certificate store that contains the existing certificates, CTLs, or CRLs to add, delete, save, or display.</span></span> <span data-ttu-id="a182d-121">這可以是存放區檔或系統存放區。</span><span class="sxs-lookup"><span data-stu-id="a182d-121">This can be a store file or a systems store.</span></span>|  
|<span data-ttu-id="a182d-122">*destinationStorename*</span><span class="sxs-lookup"><span data-stu-id="a182d-122">*destinationStorename*</span></span>|<span data-ttu-id="a182d-123">輸出憑證存放區或檔案。</span><span class="sxs-lookup"><span data-stu-id="a182d-123">The output certificate store or file.</span></span>|  
  
|<span data-ttu-id="a182d-124">選項</span><span class="sxs-lookup"><span data-stu-id="a182d-124">Option</span></span>|<span data-ttu-id="a182d-125">描述</span><span class="sxs-lookup"><span data-stu-id="a182d-125">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a182d-126">**/add**</span><span class="sxs-lookup"><span data-stu-id="a182d-126">**/add**</span></span>|<span data-ttu-id="a182d-127">將憑證、CTL 和 CRL 加入憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="a182d-127">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>|  
|<span data-ttu-id="a182d-128">**/all**</span><span class="sxs-lookup"><span data-stu-id="a182d-128">**/all**</span></span>|<span data-ttu-id="a182d-129">與 **/add** 一起使用時會加入所有項目。</span><span class="sxs-lookup"><span data-stu-id="a182d-129">Adds all entries when used with **/add**.</span></span> <span data-ttu-id="a182d-130">與 **/del** 一起使用時會刪除所有項目。未與 **/add** 或 **/del** 選項一起使用時，會顯示所有項目。</span><span class="sxs-lookup"><span data-stu-id="a182d-130">Deletes all entries when used with **/del**. Displays all entries when used without the **/add** or **/del** options.</span></span> <span data-ttu-id="a182d-131">**/all** 選項無法與 **/put** 一起使用。</span><span class="sxs-lookup"><span data-stu-id="a182d-131">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="a182d-132">**/c**</span><span class="sxs-lookup"><span data-stu-id="a182d-132">**/c**</span></span>|<span data-ttu-id="a182d-133">與 **/add** 一起使用時會加入憑證。</span><span class="sxs-lookup"><span data-stu-id="a182d-133">Adds certificates when used with **/add**.</span></span> <span data-ttu-id="a182d-134">與 **/del** 一起使用時會刪除憑證。與 **/put** 一起使用時會儲存憑證。</span><span class="sxs-lookup"><span data-stu-id="a182d-134">Deletes certificates when used with **/del**. Saves certificates when used with **/put**.</span></span> <span data-ttu-id="a182d-135">未與 **/add**、**/del** 或 **/put** 選項一起使用時，會顯示憑證。</span><span class="sxs-lookup"><span data-stu-id="a182d-135">Displays certificates when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="a182d-136">**/CRL**</span><span class="sxs-lookup"><span data-stu-id="a182d-136">**/CRL**</span></span>|<span data-ttu-id="a182d-137">與 **/add** 一起使用時會加入 CRL。</span><span class="sxs-lookup"><span data-stu-id="a182d-137">Adds CRLs when used with **/add**.</span></span> <span data-ttu-id="a182d-138">與 **/del** 一起使用時會刪除 CRL。與 **/put** 一起使用時會儲存 CRL。</span><span class="sxs-lookup"><span data-stu-id="a182d-138">Deletes CRLs when used with **/del**. Saves CRLs when used with **/put**.</span></span> <span data-ttu-id="a182d-139">未與 **/add**、**/del** 或 **/put** 選項一起使用時，會顯示 CRL。</span><span class="sxs-lookup"><span data-stu-id="a182d-139">Displays CRLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="a182d-140">**/CTL**</span><span class="sxs-lookup"><span data-stu-id="a182d-140">**/CTL**</span></span>|<span data-ttu-id="a182d-141">與 **/add** 一起使用時會加入 CTL。</span><span class="sxs-lookup"><span data-stu-id="a182d-141">Adds CTLs when used with **/add**.</span></span> <span data-ttu-id="a182d-142">與 **/del** 一起使用時會刪除 CTL。與 **/put** 一起使用時會儲存 CTL。</span><span class="sxs-lookup"><span data-stu-id="a182d-142">Deletes CTLs when used with **/del**. Saves CTLs when used with **/put**.</span></span> <span data-ttu-id="a182d-143">未與 **/add**、**/del** 或 **/put** 選項一起使用時，會顯示 CTL。</span><span class="sxs-lookup"><span data-stu-id="a182d-143">Displays CTLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="a182d-144">**/del**</span><span class="sxs-lookup"><span data-stu-id="a182d-144">**/del**</span></span>|<span data-ttu-id="a182d-145">從憑證存放區刪除憑證、CTL 和 CRL。</span><span class="sxs-lookup"><span data-stu-id="a182d-145">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>|  
|<span data-ttu-id="a182d-146">**/e** *encodingType*</span><span class="sxs-lookup"><span data-stu-id="a182d-146">**/e** *encodingType*</span></span>|<span data-ttu-id="a182d-147">指定憑證的編碼類型。</span><span class="sxs-lookup"><span data-stu-id="a182d-147">Specifies the certificate encoding type.</span></span> <span data-ttu-id="a182d-148">預設為 `X509_ASN_ENCODING`。</span><span class="sxs-lookup"><span data-stu-id="a182d-148">The default is `X509_ASN_ENCODING`.</span></span>|  
|<span data-ttu-id="a182d-149">**/f** *dwFlags*</span><span class="sxs-lookup"><span data-stu-id="a182d-149">**/f** *dwFlags*</span></span>|<span data-ttu-id="a182d-150">指定存放區的開放旗標。</span><span class="sxs-lookup"><span data-stu-id="a182d-150">Specifies the store open flag.</span></span> <span data-ttu-id="a182d-151">這是傳遞到 **CertOpenStore** 的 *dwFlags* 參數。</span><span class="sxs-lookup"><span data-stu-id="a182d-151">This is the *dwFlags* parameter passed to **CertOpenStore**.</span></span> <span data-ttu-id="a182d-152">預設值是 CERT_SYSTEM_STORE_CURRENT_USER。</span><span class="sxs-lookup"><span data-stu-id="a182d-152">The default value is CERT_SYSTEM_STORE_CURRENT_USER.</span></span> <span data-ttu-id="a182d-153">只有在使用 **/y** 選項時，才會將這個選項列入考量。</span><span class="sxs-lookup"><span data-stu-id="a182d-153">This option is considered only if the **/y** option is used.</span></span>|  
|<span data-ttu-id="a182d-154">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="a182d-154">**/h**[**elp**]</span></span>|<span data-ttu-id="a182d-155">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="a182d-155">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="a182d-156">**/n** *nam*</span><span class="sxs-lookup"><span data-stu-id="a182d-156">**/n** *nam*</span></span>|<span data-ttu-id="a182d-157">指定憑證的通用名稱來進行加入、刪除或儲存。</span><span class="sxs-lookup"><span data-stu-id="a182d-157">Specifies the common name of the certificate to add, delete, or save.</span></span> <span data-ttu-id="a182d-158">這個選項只能與憑證一起使用，無法與 CTL 或 CRL 一起使用。</span><span class="sxs-lookup"><span data-stu-id="a182d-158">This option can only be used with certificates; it cannot be used with CTLs or CRLs.</span></span>|  
|<span data-ttu-id="a182d-159">**/put**</span><span class="sxs-lookup"><span data-stu-id="a182d-159">**/put**</span></span>|<span data-ttu-id="a182d-160">將 X.509 憑證、CTL 或 CRL 從憑證存放區儲存到檔案。</span><span class="sxs-lookup"><span data-stu-id="a182d-160">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span> <span data-ttu-id="a182d-161">檔案是以 X.509 格式儲存。</span><span class="sxs-lookup"><span data-stu-id="a182d-161">The file is saved in X.509 format.</span></span> <span data-ttu-id="a182d-162">您可以將 **/7** 選項與 **/put** 選項一起使用，以 PKCS #7 格式儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="a182d-162">You can use the **/7** option with the **/put** option to save the file in PKCS #7 format.</span></span> <span data-ttu-id="a182d-163">**/put** 選項後面必須接著 **/c**、**/CTL** 或 **/CRL**</span><span class="sxs-lookup"><span data-stu-id="a182d-163">The **/put** option must be followed by either **/c**, **/CTL**, or **/CRL**.</span></span> <span data-ttu-id="a182d-164">**/all** 選項無法與 **/put** 一起使用。</span><span class="sxs-lookup"><span data-stu-id="a182d-164">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="a182d-165">**/r** *location*</span><span class="sxs-lookup"><span data-stu-id="a182d-165">**/r** *location*</span></span>|<span data-ttu-id="a182d-166">識別系統存放區的登錄位置。</span><span class="sxs-lookup"><span data-stu-id="a182d-166">Identifies the registry location of the system store.</span></span> <span data-ttu-id="a182d-167">只有在指定 **/s** 選項時，才會將這個選項列入考量。</span><span class="sxs-lookup"><span data-stu-id="a182d-167">This option is considered only if you specify the **/s** option.</span></span> <span data-ttu-id="a182d-168">*location* 必須是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="a182d-168">*location* must be one of the following:</span></span><br /><br /> <span data-ttu-id="a182d-169">-   `currentUser` 表示憑證存放區是在 HKEY_CURRENT_USER 機碼下方。</span><span class="sxs-lookup"><span data-stu-id="a182d-169">-   `currentUser` indicates that the certificate store is under the HKEY_CURRENT_USER key.</span></span> <span data-ttu-id="a182d-170">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="a182d-170">This is the default.</span></span><br /><span data-ttu-id="a182d-171">-   `localMachine` 表示憑證存放區是在 HKEY_LOCAL_MACHINE 機碼下方。</span><span class="sxs-lookup"><span data-stu-id="a182d-171">-   `localMachine` indicates that the certificate store is under the HKEY_LOCAL_MACHINE key.</span></span>|  
|<span data-ttu-id="a182d-172">**/s**</span><span class="sxs-lookup"><span data-stu-id="a182d-172">**/s**</span></span>|<span data-ttu-id="a182d-173">指示憑證存放區是一個系統存放區。</span><span class="sxs-lookup"><span data-stu-id="a182d-173">Indicates that the certificate store is a system store.</span></span> <span data-ttu-id="a182d-174">如果不指定此選項，會將存放區視為 **StoreFile**。</span><span class="sxs-lookup"><span data-stu-id="a182d-174">If you do not specify this option, the store is considered to be a **StoreFile**.</span></span>|  
|<span data-ttu-id="a182d-175">**/sha1** *sha1Hash*</span><span class="sxs-lookup"><span data-stu-id="a182d-175">**/sha1** *sha1Hash*</span></span>|<span data-ttu-id="a182d-176">指定憑證、CTL 或 CRL 的 SHA1 雜湊來進行加入、刪除或儲存。</span><span class="sxs-lookup"><span data-stu-id="a182d-176">Specifies the SHA1 hash of the certificate, CTL, or CRL to add, delete, or save.</span></span>|  
|<span data-ttu-id="a182d-177">**/v**</span><span class="sxs-lookup"><span data-stu-id="a182d-177">**/v**</span></span>|<span data-ttu-id="a182d-178">指定詳細資訊模式；顯示憑證、CTL 和 CRL 的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a182d-178">Specifies verbose mode; displays detailed information about certificates, CTLs, and CRLs.</span></span> <span data-ttu-id="a182d-179">這個選項無法與 **/add**、**/del** 或 **/put** 選項一起使用。</span><span class="sxs-lookup"><span data-stu-id="a182d-179">This option cannot be used with the **/add**, **/del**, or **/put** options.</span></span>|  
|<span data-ttu-id="a182d-180">**/y** *provider*</span><span class="sxs-lookup"><span data-stu-id="a182d-180">**/y** *provider*</span></span>|<span data-ttu-id="a182d-181">指定存放區提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="a182d-181">Specifies the store provider name.</span></span>|  
|<span data-ttu-id="a182d-182">**/7**</span><span class="sxs-lookup"><span data-stu-id="a182d-182">**/7**</span></span>|<span data-ttu-id="a182d-183">將目的存放區儲存成 PKCS #7 物件。</span><span class="sxs-lookup"><span data-stu-id="a182d-183">Saves the destination store as a PKCS #7 object.</span></span>|  
|<span data-ttu-id="a182d-184">**/?**</span><span class="sxs-lookup"><span data-stu-id="a182d-184">**/?**</span></span>|<span data-ttu-id="a182d-185">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="a182d-185">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a182d-186">備註</span><span class="sxs-lookup"><span data-stu-id="a182d-186">Remarks</span></span>  
 <span data-ttu-id="a182d-187">Certmgr.exe 會執行下列幾種基本功能：</span><span class="sxs-lookup"><span data-stu-id="a182d-187">Certmgr.exe performs the following basic functions:</span></span>  
  
-   <span data-ttu-id="a182d-188">將憑證、CTL 和 CRL 顯示到主控台。</span><span class="sxs-lookup"><span data-stu-id="a182d-188">Displays certificates, CTLs, and CRLs to the console.</span></span>  
  
-   <span data-ttu-id="a182d-189">將憑證、CTL 和 CRL 加入憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="a182d-189">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>  
  
-   <span data-ttu-id="a182d-190">從憑證存放區刪除憑證、CTL 和 CRL。</span><span class="sxs-lookup"><span data-stu-id="a182d-190">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>  
  
-   <span data-ttu-id="a182d-191">將 X.509 憑證、CTL 或 CRL 從憑證存放區儲存到檔案。</span><span class="sxs-lookup"><span data-stu-id="a182d-191">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span>  
  
 <span data-ttu-id="a182d-192">Certmgr.exe 可使用於兩種憑證存放區類型：**StoreFile** 和系統存放區。</span><span class="sxs-lookup"><span data-stu-id="a182d-192">Certmgr.exe works with two types of certificate stores: **StoreFile** and system store.</span></span> <span data-ttu-id="a182d-193">您沒有必要指定憑證存放區的類型，Certmgr.exe 會識別存放區類型，並執行適當的作業。</span><span class="sxs-lookup"><span data-stu-id="a182d-193">It is not necessary to specify the type of certificate store; Certmgr.exe can identify the store type and perform the appropriate operations.</span></span>  
  
 <span data-ttu-id="a182d-194">在沒有指定任何選項的情況下執行 Certmgr.exe 將會啟動 certmgr.msc 嵌入式管理單元，這個單元含有 GUI，會幫助憑證管理工作，您也可以從命令列使用這些憑證管理工作。</span><span class="sxs-lookup"><span data-stu-id="a182d-194">Running Certmgr.exe without specifying any options launches the certmgr.msc snap-in, which has a GUI that helps with the certificate management tasks that are also available from the command line.</span></span> <span data-ttu-id="a182d-195">GUI 提供一個可從磁碟將憑證、CTL 和 CRL 複製到憑證存放區的匯入精靈。</span><span class="sxs-lookup"><span data-stu-id="a182d-195">The GUI provides an import wizard, which copies certificates, CTLs, and CRLs from your disk to a certificate store.</span></span>  
  
 <span data-ttu-id="a182d-196">您可以編譯並執行下列程式碼以找到 X509Certificate 存放 `sourceStorename` 和 `destinationStorename` 參數的名字。</span><span class="sxs-lookup"><span data-stu-id="a182d-196">You can find the names of X509Certificate stores for the `sourceStorename` and `destinationStorename` parameters by compiling and running the following code.</span></span>  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 <span data-ttu-id="a182d-197">如需憑證的詳細資訊，請參閱[使用憑證](../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="a182d-197">For more information about certificates, see [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a182d-198">範例</span><span class="sxs-lookup"><span data-stu-id="a182d-198">Examples</span></span>  
 <span data-ttu-id="a182d-199">下列命令會顯示叫做 `my` 且具有詳細資訊輸出的預設系統存放區。</span><span class="sxs-lookup"><span data-stu-id="a182d-199">The following command displays a default system store called `my` with verbose output.</span></span>  
  
```  
certmgr /v /s my  
```  
  
 <span data-ttu-id="a182d-200">下列命令會將 `myFile.ext` 檔案中的所有憑證加入到名為 `newFile.ext` 的新檔案中。</span><span class="sxs-lookup"><span data-stu-id="a182d-200">The following command adds all the certificates in a file called `myFile.ext` to a new file called `newFile.ext`.</span></span>  
  
```  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 <span data-ttu-id="a182d-201">下列命令會將 `testcert.cer` 檔案中的憑證加入至 `my` 系統存放區。</span><span class="sxs-lookup"><span data-stu-id="a182d-201">The following command adds the certificate in a file named `testcert.cer` to the `my` system store.</span></span>  
  
```  
certmgr /add /c testcert.cer /s my  
```  
  
 <span data-ttu-id="a182d-202">下列命令會將 `TrustedCert.cer` 檔案中的憑證加入至根憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="a182d-202">The following command adds the certificate in a file named `TrustedCert.cer` to the root certificate store.</span></span>  
  
```  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 <span data-ttu-id="a182d-203">下列命令會將 `myCert` 系統存放區中通用名稱為 `my` 的憑證儲存到名為 `newCert.cer` 的檔案。</span><span class="sxs-lookup"><span data-stu-id="a182d-203">The following command saves a certificate with the common name `myCert` in the `my` system store to a file called `newCert.cer`.</span></span>  
  
```  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 <span data-ttu-id="a182d-204">下列命令會刪除 `my` 系統存放區中的所有 CTL，並將產生的存放區儲存到名為 `newStore.str` 的檔案。</span><span class="sxs-lookup"><span data-stu-id="a182d-204">The following command deletes all CTLs in the `my` system store and saves the resulting store to a file called `newStore.str`.</span></span>  
  
```  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 <span data-ttu-id="a182d-205">下列命令會將 `my` 系統存放區中的憑證儲存在 `newFile` 檔案。</span><span class="sxs-lookup"><span data-stu-id="a182d-205">The following command saves a certificate in the `my` system store in the file `newFile`.</span></span> <span data-ttu-id="a182d-206">系統會提示您輸入來自 `my` 的憑證號碼，以便放置在 `newFile` 中。</span><span class="sxs-lookup"><span data-stu-id="a182d-206">You will be prompted to enter the certificate number from `my` to put in `newFile`.</span></span>  
  
```  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a><span data-ttu-id="a182d-207">請參閱</span><span class="sxs-lookup"><span data-stu-id="a182d-207">See Also</span></span>  
 [<span data-ttu-id="a182d-208">工具</span><span class="sxs-lookup"><span data-stu-id="a182d-208">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="a182d-209">Makecert.exe (憑證建立工具)</span><span class="sxs-lookup"><span data-stu-id="a182d-209">Makecert.exe (Certificate Creation Tool)</span></span>](https://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)  
 [<span data-ttu-id="a182d-210">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="a182d-210">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
