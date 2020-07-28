---
title: Certmgr.exe (憑證管理員工具)
description: 探索憑證管理員工具 Certmgr.exe。 此工具會管理憑證、憑證信任清單（Ctl）和憑證撤銷清單（Crl）。
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
ms.openlocfilehash: 43ab281e6ec28ff23ea584b03fd4278c6682e33e
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167265"
---
# <a name="certmgrexe-certificate-manager-tool"></a><span data-ttu-id="a50d2-104">Certmgr.exe (憑證管理員工具)</span><span class="sxs-lookup"><span data-stu-id="a50d2-104">Certmgr.exe (Certificate Manager Tool)</span></span>
<span data-ttu-id="a50d2-105">憑證管理員工具 (Certmgr.exe) 可以管理憑證、憑證信任清單 (CTL) 和憑證撤銷清單 (CRL)。</span><span class="sxs-lookup"><span data-stu-id="a50d2-105">The Certificate Manager tool (Certmgr.exe) manages certificates, certificate trust lists (CTLs), and certificate revocation lists (CRLs).</span></span>  
  
 <span data-ttu-id="a50d2-106">憑證管理員會隨 Visual Studio 自動安裝。</span><span class="sxs-lookup"><span data-stu-id="a50d2-106">The Certificate Manager is automatically installed with Visual Studio.</span></span> <span data-ttu-id="a50d2-107">若要啟動工具，請使用[命令提示字元](developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="a50d2-107">To start the tool, use the [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a50d2-108">憑證管理工具 (Certmgr.exe) 是一個命令列公用程式，而憑證 (Certmgr.msc) 則是 Microsoft Management Console (MMC) 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="a50d2-108">The Certificate Manager tool (Certmgr.exe) is a command-line utility, whereas Certificates (Certmgr.msc) is a Microsoft Management Console (MMC) snap-in.</span></span> <span data-ttu-id="a50d2-109">因為 Certmgr.msc 通常會位於 Windows 系統目錄中，以在命令列中輸入 `certmgr` 可能會載入憑證 MMC 嵌入式管理單元，即使您已開啟 Visual Studio 開發人員命令提示字元也一樣。</span><span class="sxs-lookup"><span data-stu-id="a50d2-109">Because Certmgr.msc is usually found in the Windows System directory, entering `certmgr` at the command line may load the Certificates MMC snap-in even if you have opened the Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="a50d2-110">發生這種情況是因為嵌入式管理單元的路徑在 PATH 環境變數中位於憑證管理員工具的路徑之前。</span><span class="sxs-lookup"><span data-stu-id="a50d2-110">This occurs because the path to the snap-in precedes the path to the Certificate Manager tool in the PATH environment variable.</span></span> <span data-ttu-id="a50d2-111">如果您遇到此問題，可以透過指定可執行檔的路徑來執行 Certmgr.exe 指令。</span><span class="sxs-lookup"><span data-stu-id="a50d2-111">If you encounter this problem, you can execute Certmgr.exe commands by specifying the path to the executable.</span></span>  
  
 <span data-ttu-id="a50d2-112">此工具會自動與 Visual Studio 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="a50d2-112">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="a50d2-113">若要執行這項工具，請使用 [Visual Studio 開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。</span><span class="sxs-lookup"><span data-stu-id="a50d2-113">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="a50d2-114">如需詳細資訊，請參閱[命令提示字元](developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="a50d2-114">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="a50d2-115">如需 X.509 憑證的概觀，請參閱[使用憑證](../wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="a50d2-115">For an overview of X.509 certificates, see [Working with Certificates](../wcf/feature-details/working-with-certificates.md).</span></span>  
  
 <span data-ttu-id="a50d2-116">在命令提示字元中，請輸入下列項目：</span><span class="sxs-lookup"><span data-stu-id="a50d2-116">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a50d2-117">語法</span><span class="sxs-lookup"><span data-stu-id="a50d2-117">Syntax</span></span>  
  
```console  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
## <a name="parameters"></a><span data-ttu-id="a50d2-118">參數</span><span class="sxs-lookup"><span data-stu-id="a50d2-118">Parameters</span></span>  
  
|<span data-ttu-id="a50d2-119">引數</span><span class="sxs-lookup"><span data-stu-id="a50d2-119">Argument</span></span>|<span data-ttu-id="a50d2-120">描述</span><span class="sxs-lookup"><span data-stu-id="a50d2-120">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="a50d2-121">*sourceStorename*</span><span class="sxs-lookup"><span data-stu-id="a50d2-121">*sourceStorename*</span></span>|<span data-ttu-id="a50d2-122">憑證存放區，包含現有的憑證、CTL，或是要新增、刪除、儲存或顯示的 CRL。</span><span class="sxs-lookup"><span data-stu-id="a50d2-122">The certificate store that contains the existing certificates, CTLs, or CRLs to add, delete, save, or display.</span></span> <span data-ttu-id="a50d2-123">這可以是存放區檔或系統存放區。</span><span class="sxs-lookup"><span data-stu-id="a50d2-123">This can be a store file or a systems store.</span></span>|  
|<span data-ttu-id="a50d2-124">*destinationStorename*</span><span class="sxs-lookup"><span data-stu-id="a50d2-124">*destinationStorename*</span></span>|<span data-ttu-id="a50d2-125">輸出憑證存放區或檔案。</span><span class="sxs-lookup"><span data-stu-id="a50d2-125">The output certificate store or file.</span></span>|  
  
|<span data-ttu-id="a50d2-126">選項</span><span class="sxs-lookup"><span data-stu-id="a50d2-126">Option</span></span>|<span data-ttu-id="a50d2-127">描述</span><span class="sxs-lookup"><span data-stu-id="a50d2-127">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a50d2-128">**/add**</span><span class="sxs-lookup"><span data-stu-id="a50d2-128">**/add**</span></span>|<span data-ttu-id="a50d2-129">將憑證、CTL 和 CRL 加入憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="a50d2-129">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>|  
|<span data-ttu-id="a50d2-130">**/all**</span><span class="sxs-lookup"><span data-stu-id="a50d2-130">**/all**</span></span>|<span data-ttu-id="a50d2-131">與 **/add** 一起使用時會加入所有項目。</span><span class="sxs-lookup"><span data-stu-id="a50d2-131">Adds all entries when used with **/add**.</span></span> <span data-ttu-id="a50d2-132">當與 **/del**搭配使用時，刪除所有專案。在未使用 **/add**或 **/del**選項的情況下，顯示所有專案。</span><span class="sxs-lookup"><span data-stu-id="a50d2-132">Deletes all entries when used with **/del**. Displays all entries when used without the **/add** or **/del** options.</span></span> <span data-ttu-id="a50d2-133">**/all** 選項無法與 **/put** 一起使用。</span><span class="sxs-lookup"><span data-stu-id="a50d2-133">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="a50d2-134">**/c**</span><span class="sxs-lookup"><span data-stu-id="a50d2-134">**/c**</span></span>|<span data-ttu-id="a50d2-135">與 **/add** 一起使用時會加入憑證。</span><span class="sxs-lookup"><span data-stu-id="a50d2-135">Adds certificates when used with **/add**.</span></span> <span data-ttu-id="a50d2-136">與 **/del**搭配使用時，會刪除憑證。會在與 **/put**搭配使用時儲存憑證。</span><span class="sxs-lookup"><span data-stu-id="a50d2-136">Deletes certificates when used with **/del**. Saves certificates when used with **/put**.</span></span> <span data-ttu-id="a50d2-137">未與 **/add**、**/del** 或 **/put** 選項一起使用時，會顯示憑證。</span><span class="sxs-lookup"><span data-stu-id="a50d2-137">Displays certificates when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="a50d2-138">**/CRL**</span><span class="sxs-lookup"><span data-stu-id="a50d2-138">**/CRL**</span></span>|<span data-ttu-id="a50d2-139">與 **/add** 一起使用時會加入 CRL。</span><span class="sxs-lookup"><span data-stu-id="a50d2-139">Adds CRLs when used with **/add**.</span></span> <span data-ttu-id="a50d2-140">與 **/del**搭配使用時，刪除 crl。與 **/put**搭配使用時，會儲存 crl。</span><span class="sxs-lookup"><span data-stu-id="a50d2-140">Deletes CRLs when used with **/del**. Saves CRLs when used with **/put**.</span></span> <span data-ttu-id="a50d2-141">未與 **/add**、**/del** 或 **/put** 選項一起使用時，會顯示 CRL。</span><span class="sxs-lookup"><span data-stu-id="a50d2-141">Displays CRLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="a50d2-142">**/CTL**</span><span class="sxs-lookup"><span data-stu-id="a50d2-142">**/CTL**</span></span>|<span data-ttu-id="a50d2-143">與 **/add** 一起使用時會加入 CTL。</span><span class="sxs-lookup"><span data-stu-id="a50d2-143">Adds CTLs when used with **/add**.</span></span> <span data-ttu-id="a50d2-144">與 **/del**搭配使用時，會刪除 ctl。與 **/put**搭配使用時，會儲存 ctl。</span><span class="sxs-lookup"><span data-stu-id="a50d2-144">Deletes CTLs when used with **/del**. Saves CTLs when used with **/put**.</span></span> <span data-ttu-id="a50d2-145">未與 **/add**、**/del** 或 **/put** 選項一起使用時，會顯示 CTL。</span><span class="sxs-lookup"><span data-stu-id="a50d2-145">Displays CTLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="a50d2-146">**/del**</span><span class="sxs-lookup"><span data-stu-id="a50d2-146">**/del**</span></span>|<span data-ttu-id="a50d2-147">從憑證存放區刪除憑證、CTL 和 CRL。</span><span class="sxs-lookup"><span data-stu-id="a50d2-147">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>|  
|<span data-ttu-id="a50d2-148">**/e** *encodingType*</span><span class="sxs-lookup"><span data-stu-id="a50d2-148">**/e** *encodingType*</span></span>|<span data-ttu-id="a50d2-149">指定憑證的編碼類型。</span><span class="sxs-lookup"><span data-stu-id="a50d2-149">Specifies the certificate encoding type.</span></span> <span data-ttu-id="a50d2-150">預設為 `X509_ASN_ENCODING`。</span><span class="sxs-lookup"><span data-stu-id="a50d2-150">The default is `X509_ASN_ENCODING`.</span></span>|  
|<span data-ttu-id="a50d2-151">**/f** *dwFlags*</span><span class="sxs-lookup"><span data-stu-id="a50d2-151">**/f** *dwFlags*</span></span>|<span data-ttu-id="a50d2-152">指定存放區的開放旗標。</span><span class="sxs-lookup"><span data-stu-id="a50d2-152">Specifies the store open flag.</span></span> <span data-ttu-id="a50d2-153">這是傳遞到 **CertOpenStore** 的 *dwFlags* 參數。</span><span class="sxs-lookup"><span data-stu-id="a50d2-153">This is the *dwFlags* parameter passed to **CertOpenStore**.</span></span> <span data-ttu-id="a50d2-154">預設值是 CERT_SYSTEM_STORE_CURRENT_USER。</span><span class="sxs-lookup"><span data-stu-id="a50d2-154">The default value is CERT_SYSTEM_STORE_CURRENT_USER.</span></span> <span data-ttu-id="a50d2-155">只有在使用 **/y** 選項時，才會將這個選項列入考量。</span><span class="sxs-lookup"><span data-stu-id="a50d2-155">This option is considered only if the **/y** option is used.</span></span>|  
|<span data-ttu-id="a50d2-156">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="a50d2-156">**/h**[**elp**]</span></span>|<span data-ttu-id="a50d2-157">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="a50d2-157">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="a50d2-158">**/n** *nam*</span><span class="sxs-lookup"><span data-stu-id="a50d2-158">**/n** *nam*</span></span>|<span data-ttu-id="a50d2-159">指定憑證的通用名稱來進行加入、刪除或儲存。</span><span class="sxs-lookup"><span data-stu-id="a50d2-159">Specifies the common name of the certificate to add, delete, or save.</span></span> <span data-ttu-id="a50d2-160">這個選項只能與憑證一起使用，無法與 CTL 或 CRL 一起使用。</span><span class="sxs-lookup"><span data-stu-id="a50d2-160">This option can only be used with certificates; it cannot be used with CTLs or CRLs.</span></span>|  
|<span data-ttu-id="a50d2-161">**/put**</span><span class="sxs-lookup"><span data-stu-id="a50d2-161">**/put**</span></span>|<span data-ttu-id="a50d2-162">將 X.509 憑證、CTL 或 CRL 從憑證存放區儲存到檔案。</span><span class="sxs-lookup"><span data-stu-id="a50d2-162">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span> <span data-ttu-id="a50d2-163">檔案是以 X.509 格式儲存。</span><span class="sxs-lookup"><span data-stu-id="a50d2-163">The file is saved in X.509 format.</span></span> <span data-ttu-id="a50d2-164">您可以將 **/7** 選項與 **/put** 選項一起使用，以 PKCS #7 格式儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="a50d2-164">You can use the **/7** option with the **/put** option to save the file in PKCS #7 format.</span></span> <span data-ttu-id="a50d2-165">**/put** 選項後面必須接著 **/c**、**/CTL** 或 **/CRL**</span><span class="sxs-lookup"><span data-stu-id="a50d2-165">The **/put** option must be followed by either **/c**, **/CTL**, or **/CRL**.</span></span> <span data-ttu-id="a50d2-166">**/all** 選項無法與 **/put** 一起使用。</span><span class="sxs-lookup"><span data-stu-id="a50d2-166">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="a50d2-167">**/r** *location*</span><span class="sxs-lookup"><span data-stu-id="a50d2-167">**/r** *location*</span></span>|<span data-ttu-id="a50d2-168">識別系統存放區的登錄位置。</span><span class="sxs-lookup"><span data-stu-id="a50d2-168">Identifies the registry location of the system store.</span></span> <span data-ttu-id="a50d2-169">只有在指定 **/s** 選項時，才會將這個選項列入考量。</span><span class="sxs-lookup"><span data-stu-id="a50d2-169">This option is considered only if you specify the **/s** option.</span></span> <span data-ttu-id="a50d2-170">*location* 必須是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="a50d2-170">*location* must be one of the following:</span></span><br /><br /> <span data-ttu-id="a50d2-171">-   `currentUser` 表示憑證存放區是在 HKEY_CURRENT_USER 機碼下方。</span><span class="sxs-lookup"><span data-stu-id="a50d2-171">-   `currentUser` indicates that the certificate store is under the HKEY_CURRENT_USER key.</span></span> <span data-ttu-id="a50d2-172">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="a50d2-172">This is the default.</span></span><br /><span data-ttu-id="a50d2-173">-   `localMachine` 表示憑證存放區是在 HKEY_LOCAL_MACHINE 機碼下方。</span><span class="sxs-lookup"><span data-stu-id="a50d2-173">-   `localMachine` indicates that the certificate store is under the HKEY_LOCAL_MACHINE key.</span></span>|  
|<span data-ttu-id="a50d2-174">**/s**</span><span class="sxs-lookup"><span data-stu-id="a50d2-174">**/s**</span></span>|<span data-ttu-id="a50d2-175">指示憑證存放區是一個系統存放區。</span><span class="sxs-lookup"><span data-stu-id="a50d2-175">Indicates that the certificate store is a system store.</span></span> <span data-ttu-id="a50d2-176">如果不指定此選項，會將存放區視為 **StoreFile**。</span><span class="sxs-lookup"><span data-stu-id="a50d2-176">If you do not specify this option, the store is considered to be a **StoreFile**.</span></span>|  
|<span data-ttu-id="a50d2-177">**/sha1** *sha1Hash*</span><span class="sxs-lookup"><span data-stu-id="a50d2-177">**/sha1** *sha1Hash*</span></span>|<span data-ttu-id="a50d2-178">指定憑證、CTL 或 CRL 的 SHA1 雜湊來進行加入、刪除或儲存。</span><span class="sxs-lookup"><span data-stu-id="a50d2-178">Specifies the SHA1 hash of the certificate, CTL, or CRL to add, delete, or save.</span></span>|  
|<span data-ttu-id="a50d2-179">**/v**</span><span class="sxs-lookup"><span data-stu-id="a50d2-179">**/v**</span></span>|<span data-ttu-id="a50d2-180">指定詳細資訊模式；顯示憑證、CTL 和 CRL 的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a50d2-180">Specifies verbose mode; displays detailed information about certificates, CTLs, and CRLs.</span></span> <span data-ttu-id="a50d2-181">這個選項無法與 **/add**、**/del** 或 **/put** 選項一起使用。</span><span class="sxs-lookup"><span data-stu-id="a50d2-181">This option cannot be used with the **/add**, **/del**, or **/put** options.</span></span>|  
|<span data-ttu-id="a50d2-182">**/y** *provider*</span><span class="sxs-lookup"><span data-stu-id="a50d2-182">**/y** *provider*</span></span>|<span data-ttu-id="a50d2-183">指定存放區提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="a50d2-183">Specifies the store provider name.</span></span>|  
|<span data-ttu-id="a50d2-184">**/7**</span><span class="sxs-lookup"><span data-stu-id="a50d2-184">**/7**</span></span>|<span data-ttu-id="a50d2-185">將目的存放區儲存成 PKCS #7 物件。</span><span class="sxs-lookup"><span data-stu-id="a50d2-185">Saves the destination store as a PKCS #7 object.</span></span>|  
|<span data-ttu-id="a50d2-186">**/?**</span><span class="sxs-lookup"><span data-stu-id="a50d2-186">**/?**</span></span>|<span data-ttu-id="a50d2-187">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="a50d2-187">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a50d2-188">備註</span><span class="sxs-lookup"><span data-stu-id="a50d2-188">Remarks</span></span>  
 <span data-ttu-id="a50d2-189">Certmgr.exe 會執行下列幾種基本功能：</span><span class="sxs-lookup"><span data-stu-id="a50d2-189">Certmgr.exe performs the following basic functions:</span></span>  
  
- <span data-ttu-id="a50d2-190">將憑證、CTL 和 CRL 顯示到主控台。</span><span class="sxs-lookup"><span data-stu-id="a50d2-190">Displays certificates, CTLs, and CRLs to the console.</span></span>  
  
- <span data-ttu-id="a50d2-191">將憑證、CTL 和 CRL 加入憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="a50d2-191">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>  
  
- <span data-ttu-id="a50d2-192">從憑證存放區刪除憑證、CTL 和 CRL。</span><span class="sxs-lookup"><span data-stu-id="a50d2-192">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>  
  
- <span data-ttu-id="a50d2-193">將 X.509 憑證、CTL 或 CRL 從憑證存放區儲存到檔案。</span><span class="sxs-lookup"><span data-stu-id="a50d2-193">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span>  
  
 <span data-ttu-id="a50d2-194">Certmgr.exe 可使用於兩種憑證存放區類型：**StoreFile** 和系統存放區。</span><span class="sxs-lookup"><span data-stu-id="a50d2-194">Certmgr.exe works with two types of certificate stores: **StoreFile** and system store.</span></span> <span data-ttu-id="a50d2-195">您沒有必要指定憑證存放區的類型，Certmgr.exe 會識別存放區類型，並執行適當的作業。</span><span class="sxs-lookup"><span data-stu-id="a50d2-195">It is not necessary to specify the type of certificate store; Certmgr.exe can identify the store type and perform the appropriate operations.</span></span>  
  
 <span data-ttu-id="a50d2-196">在沒有指定任何選項的情況下執行 Certmgr.exe 將會啟動 certmgr.msc 嵌入式管理單元，這個單元含有 GUI，會幫助憑證管理工作，您也可以從命令列使用這些憑證管理工作。</span><span class="sxs-lookup"><span data-stu-id="a50d2-196">Running Certmgr.exe without specifying any options launches the certmgr.msc snap-in, which has a GUI that helps with the certificate management tasks that are also available from the command line.</span></span> <span data-ttu-id="a50d2-197">GUI 提供一個可從磁碟將憑證、CTL 和 CRL 複製到憑證存放區的匯入精靈。</span><span class="sxs-lookup"><span data-stu-id="a50d2-197">The GUI provides an import wizard, which copies certificates, CTLs, and CRLs from your disk to a certificate store.</span></span>  
  
 <span data-ttu-id="a50d2-198">您可以編譯並執行下列程式碼以找到 X509Certificate 存放 `sourceStorename` 和 `destinationStorename` 參數的名字。</span><span class="sxs-lookup"><span data-stu-id="a50d2-198">You can find the names of X509Certificate stores for the `sourceStorename` and `destinationStorename` parameters by compiling and running the following code.</span></span>  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 <span data-ttu-id="a50d2-199">如需憑證的詳細資訊，請參閱[使用憑證](../wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="a50d2-199">For more information about certificates, see [Working with Certificates](../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a50d2-200">範例</span><span class="sxs-lookup"><span data-stu-id="a50d2-200">Examples</span></span>  
 <span data-ttu-id="a50d2-201">下列命令會顯示叫做 `my` 且具有詳細資訊輸出的預設系統存放區。</span><span class="sxs-lookup"><span data-stu-id="a50d2-201">The following command displays a default system store called `my` with verbose output.</span></span>  
  
```console  
certmgr /v /s my  
```  
  
 <span data-ttu-id="a50d2-202">下列命令會將 `myFile.ext` 檔案中的所有憑證加入到名為 `newFile.ext` 的新檔案中。</span><span class="sxs-lookup"><span data-stu-id="a50d2-202">The following command adds all the certificates in a file called `myFile.ext` to a new file called `newFile.ext`.</span></span>  
  
```console  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 <span data-ttu-id="a50d2-203">下列命令會將 `testcert.cer` 檔案中的憑證加入至 `my` 系統存放區。</span><span class="sxs-lookup"><span data-stu-id="a50d2-203">The following command adds the certificate in a file named `testcert.cer` to the `my` system store.</span></span>  
  
```console  
certmgr /add /c testcert.cer /s my  
```  
  
 <span data-ttu-id="a50d2-204">下列命令會將 `TrustedCert.cer` 檔案中的憑證加入至根憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="a50d2-204">The following command adds the certificate in a file named `TrustedCert.cer` to the root certificate store.</span></span>  
  
```console  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 <span data-ttu-id="a50d2-205">下列命令會將 `myCert` 系統存放區中通用名稱為 `my` 的憑證儲存到名為 `newCert.cer` 的檔案。</span><span class="sxs-lookup"><span data-stu-id="a50d2-205">The following command saves a certificate with the common name `myCert` in the `my` system store to a file called `newCert.cer`.</span></span>  
  
```console  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 <span data-ttu-id="a50d2-206">下列命令會刪除 `my` 系統存放區中的所有 CTL，並將產生的存放區儲存到名為 `newStore.str` 的檔案。</span><span class="sxs-lookup"><span data-stu-id="a50d2-206">The following command deletes all CTLs in the `my` system store and saves the resulting store to a file called `newStore.str`.</span></span>  
  
```console  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 <span data-ttu-id="a50d2-207">下列命令會將 `my` 系統存放區中的憑證儲存在 `newFile` 檔案。</span><span class="sxs-lookup"><span data-stu-id="a50d2-207">The following command saves a certificate in the `my` system store in the file `newFile`.</span></span> <span data-ttu-id="a50d2-208">系統會提示您輸入來自 `my` 的憑證號碼，以便放置在 `newFile` 中。</span><span class="sxs-lookup"><span data-stu-id="a50d2-208">You will be prompted to enter the certificate number from `my` to put in `newFile`.</span></span>  
  
```console  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a><span data-ttu-id="a50d2-209">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a50d2-209">See also</span></span>

- [<span data-ttu-id="a50d2-210">工具</span><span class="sxs-lookup"><span data-stu-id="a50d2-210">Tools</span></span>](index.md)
- [<span data-ttu-id="a50d2-211">Makecert.exe (憑證建立工具)</span><span class="sxs-lookup"><span data-stu-id="a50d2-211">Makecert.exe (Certificate Creation Tool)</span></span>](/windows/desktop/SecCrypto/makecert)
- [<span data-ttu-id="a50d2-212">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="a50d2-212">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
