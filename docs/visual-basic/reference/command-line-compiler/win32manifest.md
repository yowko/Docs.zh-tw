---
title: -win32manifest (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 901ea984a8e8e90329953a8936e68f2fc07f8847
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="-win32manifest-visual-basic"></a><span data-ttu-id="ac1a2-102">-win32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac1a2-102">-win32manifest (Visual Basic)</span></span>
<span data-ttu-id="ac1a2-103">識別要內嵌到專案的可攜式執行檔 (PE) 中的使用者定義 Win32 應用程式資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="ac1a2-103">Identifies a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac1a2-104">語法</span><span class="sxs-lookup"><span data-stu-id="ac1a2-104">Syntax</span></span>  
  
```  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a><span data-ttu-id="ac1a2-105">引數</span><span class="sxs-lookup"><span data-stu-id="ac1a2-105">Arguments</span></span>  
  
|<span data-ttu-id="ac1a2-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="ac1a2-106">Term</span></span>|<span data-ttu-id="ac1a2-107">定義</span><span class="sxs-lookup"><span data-stu-id="ac1a2-107">Definition</span></span>|  
|---|---|  
|`fileName`|<span data-ttu-id="ac1a2-108">自訂資訊清單檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="ac1a2-108">The path of the custom manifest file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac1a2-109">備註</span><span class="sxs-lookup"><span data-stu-id="ac1a2-109">Remarks</span></span>  
 <span data-ttu-id="ac1a2-110">根據預設，Visual Basic 編譯器會將內嵌指定 asInvoker 要求的執行層級的應用程式資訊清單。</span><span class="sxs-lookup"><span data-stu-id="ac1a2-110">By default, the Visual Basic compiler embeds an application manifest that specifies a requested execution level of asInvoker.</span></span> <span data-ttu-id="ac1a2-111">它會建立資訊清單中的可執行檔建置時，通常是 bin\Debug 或是 bin\Release 資料夾當您使用 Visual Studio 的相同資料夾中。</span><span class="sxs-lookup"><span data-stu-id="ac1a2-111">It creates the manifest in the same folder in which the executable file is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="ac1a2-112">如果您想要提供自訂資訊清單，例如若要指定要求的執行層級 highestAvailable 或 requireAdministrator，使用此選項來指定檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="ac1a2-112">If you want to supply a custom manifest, for example to specify a requested execution level of highestAvailable or requireAdministrator, use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac1a2-113">此選項和[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)選項互斥。</span><span class="sxs-lookup"><span data-stu-id="ac1a2-113">This option and the [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) option are mutually exclusive.</span></span> <span data-ttu-id="ac1a2-114">如果您嘗試在相同的命令列中使用這兩個選項，就會發生建置錯誤。</span><span class="sxs-lookup"><span data-stu-id="ac1a2-114">If you try to use both options in the same command line, you will get a build error.</span></span>  
  
 <span data-ttu-id="ac1a2-115">如果應用程式的應用程式資訊清單未指定要求的執行層級，則會受限於 Windows Vista 中「使用者帳戶控制」功能下的檔案/登錄虛擬化。</span><span class="sxs-lookup"><span data-stu-id="ac1a2-115">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows Vista.</span></span> <span data-ttu-id="ac1a2-116">如需虛擬化的詳細資訊，請參閱[ClickOnce 部署在 Windows Vista 上](/visualstudio/deployment/clickonce-deployment-on-windows-vista)。</span><span class="sxs-lookup"><span data-stu-id="ac1a2-116">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="ac1a2-117">如果其中一個的下列條件成立，您的應用程式都會受到虛擬化：</span><span class="sxs-lookup"><span data-stu-id="ac1a2-117">Your application will be subject to virtualization if either of the following conditions is true:</span></span>  
  
1.  <span data-ttu-id="ac1a2-118">您使用`-nowin32manifest`選項，且未提供的資訊清單中的更新版本的建置步驟或做為 Windows 資源 (.res) 檔案的一部分使用`-win32resource`選項。</span><span class="sxs-lookup"><span data-stu-id="ac1a2-118">You use the `-nowin32manifest` option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the `-win32resource` option.</span></span>  
  
2.  <span data-ttu-id="ac1a2-119">您可以提供未指定所要求執行層級的自訂資訊清單。</span><span class="sxs-lookup"><span data-stu-id="ac1a2-119">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 <span data-ttu-id="ac1a2-120">Visual Studio 會建立預設.manifest 檔案，並將它儲存在與可執行檔在一起的偵錯和發行目錄。</span><span class="sxs-lookup"><span data-stu-id="ac1a2-120">Visual Studio creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="ac1a2-121">您可以檢視，或按一下 編輯預設 app.manifest 檔案**檢視 UAC 設定**上**應用程式**專案設計工具中的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ac1a2-121">You can view or edit the default app.manifest file by clicking **View UAC Settings** on the **Application** tab in the Project Designer.</span></span> <span data-ttu-id="ac1a2-122">如需詳細資訊，請參閱[專案設計工具、應用程式頁 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="ac1a2-122">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="ac1a2-123">您可以使用提供的應用程式資訊清單做為自訂建置後步驟，或做為 Win32 資源檔的一部分`-nowin32manifest`選項。</span><span class="sxs-lookup"><span data-stu-id="ac1a2-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the `-nowin32manifest` option.</span></span> <span data-ttu-id="ac1a2-124">如果您想要應用程式受制於 Windows Vista 上的檔案或登錄虛擬化，請使用這個相同的選項。</span><span class="sxs-lookup"><span data-stu-id="ac1a2-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="ac1a2-125">如此可防止編譯器建立和內嵌 PE 檔中的預設資訊清單。</span><span class="sxs-lookup"><span data-stu-id="ac1a2-125">This will prevent the compiler from creating and embedding a default manifest in the PE file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac1a2-126">範例</span><span class="sxs-lookup"><span data-stu-id="ac1a2-126">Example</span></span>  
 <span data-ttu-id="ac1a2-127">下列範例會示範 Visual Basic 編譯器插入 PE 預設資訊清單。</span><span class="sxs-lookup"><span data-stu-id="ac1a2-127">The following example shows the default manifest that the Visual Basic compiler inserts into a PE.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac1a2-128">編譯器會插入到資訊清單 XML 的標準應用程式名稱 MyApplication.app。</span><span class="sxs-lookup"><span data-stu-id="ac1a2-128">The compiler inserts a standard application name MyApplication.app into the manifest XML.</span></span> <span data-ttu-id="ac1a2-129">這是讓應用程式在 Windows Server 2003 Service Pack 3 上執行的因應措施。</span><span class="sxs-lookup"><span data-stu-id="ac1a2-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac1a2-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac1a2-130">See Also</span></span>  
 [<span data-ttu-id="ac1a2-131">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="ac1a2-131">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="ac1a2-132">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac1a2-132">-nowin32manifest (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
