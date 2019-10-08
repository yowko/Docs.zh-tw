---
title: -win32manifest （Visual Basic）
ms.date: 03/13/2018
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
ms.openlocfilehash: cae6b34aadf6698a337e52aa1ea1ce44206836ac
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004620"
---
# <a name="-win32manifest-visual-basic"></a><span data-ttu-id="ca656-102">-win32manifest （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="ca656-102">-win32manifest (Visual Basic)</span></span>
<span data-ttu-id="ca656-103">識別要內嵌到專案的可攜式執行檔 (PE) 中的使用者定義 Win32 應用程式資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="ca656-103">Identifies a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca656-104">語法</span><span class="sxs-lookup"><span data-stu-id="ca656-104">Syntax</span></span>  
  
```console  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a><span data-ttu-id="ca656-105">引數</span><span class="sxs-lookup"><span data-stu-id="ca656-105">Arguments</span></span>  
  
|<span data-ttu-id="ca656-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="ca656-106">Term</span></span>|<span data-ttu-id="ca656-107">定義</span><span class="sxs-lookup"><span data-stu-id="ca656-107">Definition</span></span>|  
|---|---|  
|`fileName`|<span data-ttu-id="ca656-108">自訂資訊清單檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="ca656-108">The path of the custom manifest file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca656-109">備註</span><span class="sxs-lookup"><span data-stu-id="ca656-109">Remarks</span></span>  
 <span data-ttu-id="ca656-110">根據預設，Visual Basic 編譯器會內嵌應用程式資訊清單，以指定所要求的執行層級 asInvoker。</span><span class="sxs-lookup"><span data-stu-id="ca656-110">By default, the Visual Basic compiler embeds an application manifest that specifies a requested execution level of asInvoker.</span></span> <span data-ttu-id="ca656-111">它會在建立可執行檔的相同資料夾中建立資訊清單，通常是使用 Visual Studio 時的 bin\Debug 或 bin\Release 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ca656-111">It creates the manifest in the same folder in which the executable file is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="ca656-112">如果您想要提供自訂資訊清單，例如若要指定要求的執行層級為 highestAvailable 或 requireAdministrator，請使用此選項來指定檔案名。</span><span class="sxs-lookup"><span data-stu-id="ca656-112">If you want to supply a custom manifest, for example to specify a requested execution level of highestAvailable or requireAdministrator, use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ca656-113">此選項和[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)選項是互斥的。</span><span class="sxs-lookup"><span data-stu-id="ca656-113">This option and the [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) option are mutually exclusive.</span></span> <span data-ttu-id="ca656-114">如果您嘗試在相同的命令列中使用這兩個選項，您將會收到組建錯誤。</span><span class="sxs-lookup"><span data-stu-id="ca656-114">If you try to use both options in the same command line, you will get a build error.</span></span>  
  
 <span data-ttu-id="ca656-115">如果應用程式的應用程式資訊清單未指定要求的執行層級，則會受限於 Windows Vista 中「使用者帳戶控制」功能下的檔案/登錄虛擬化。</span><span class="sxs-lookup"><span data-stu-id="ca656-115">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows Vista.</span></span> <span data-ttu-id="ca656-116">如需虛擬化的詳細資訊，請參閱[Windows Vista 上的 ClickOnce 部署](/visualstudio/deployment/clickonce-deployment-on-windows-vista)。</span><span class="sxs-lookup"><span data-stu-id="ca656-116">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="ca656-117">如果下列其中一個條件成立，則您的應用程式會受限於虛擬化：</span><span class="sxs-lookup"><span data-stu-id="ca656-117">Your application will be subject to virtualization if either of the following conditions is true:</span></span>  
  
1. <span data-ttu-id="ca656-118">您可以使用 `-nowin32manifest` 選項，而且您不會在稍後的組建步驟中提供資訊清單，或使用 `-win32resource` 選項，在 Windows 資源（.res）檔案的一部分。</span><span class="sxs-lookup"><span data-stu-id="ca656-118">You use the `-nowin32manifest` option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the `-win32resource` option.</span></span>  
  
2. <span data-ttu-id="ca656-119">您可以提供未指定所要求執行層級的自訂資訊清單。</span><span class="sxs-lookup"><span data-stu-id="ca656-119">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 <span data-ttu-id="ca656-120">Visual Studio 會建立預設.manifest 檔案，並將它與可執行檔一起儲存在偵錯和發行目錄中。</span><span class="sxs-lookup"><span data-stu-id="ca656-120">Visual Studio creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="ca656-121">您可以在 [專案設計工具] 的 [**應用程式**] 索引標籤上，按一下 [**查看 UAC 設定**]，以查看或編輯預設的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ca656-121">You can view or edit the default app.manifest file by clicking **View UAC Settings** on the **Application** tab in the Project Designer.</span></span> <span data-ttu-id="ca656-122">如需詳細資訊，請參閱[專案設計工具、應用程式頁 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="ca656-122">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="ca656-123">您可以使用 `-nowin32manifest` 選項，提供應用程式資訊清單作為自訂的後置建立步驟或 Win32 資源檔的一部分。</span><span class="sxs-lookup"><span data-stu-id="ca656-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the `-nowin32manifest` option.</span></span> <span data-ttu-id="ca656-124">如果您想要應用程式受制於 Windows Vista 上的檔案或登錄虛擬化，請使用這個相同的選項。</span><span class="sxs-lookup"><span data-stu-id="ca656-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="ca656-125">這會防止編譯器在 PE 檔案中建立和內嵌預設資訊清單。</span><span class="sxs-lookup"><span data-stu-id="ca656-125">This will prevent the compiler from creating and embedding a default manifest in the PE file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca656-126">範例</span><span class="sxs-lookup"><span data-stu-id="ca656-126">Example</span></span>  
 <span data-ttu-id="ca656-127">下列範例顯示 Visual Basic 編譯器插入 PE 的預設資訊清單。</span><span class="sxs-lookup"><span data-stu-id="ca656-127">The following example shows the default manifest that the Visual Basic compiler inserts into a PE.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ca656-128">編譯器會將標準應用程式名稱 MyApplication 插入資訊清單 XML。</span><span class="sxs-lookup"><span data-stu-id="ca656-128">The compiler inserts a standard application name MyApplication.app into the manifest XML.</span></span> <span data-ttu-id="ca656-129">這是讓應用程式在 Windows Server 2003 Service Pack 3 上執行的因應措施。</span><span class="sxs-lookup"><span data-stu-id="ca656-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ca656-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca656-130">See also</span></span>

- [<span data-ttu-id="ca656-131">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="ca656-131">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="ca656-132">-nowin32manifest （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="ca656-132">-nowin32manifest (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
