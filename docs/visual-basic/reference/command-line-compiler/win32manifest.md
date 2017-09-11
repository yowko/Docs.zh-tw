---
title: "/win32manifest (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4a9693bd7eb03dee5a2a9f2d43360b963e9fd876
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="win32manifest-visual-basic"></a><span data-ttu-id="80e7d-102">/win32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80e7d-102">/win32manifest (Visual Basic)</span></span>
<span data-ttu-id="80e7d-103">識別要內嵌到專案的可攜式執行檔 (PE) 中的使用者定義 Win32 應用程式資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="80e7d-103">Identifies a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80e7d-104">語法</span><span class="sxs-lookup"><span data-stu-id="80e7d-104">Syntax</span></span>  
  
```  
/win32manifest: fileName  
```  
  
## <a name="arguments"></a><span data-ttu-id="80e7d-105">引數</span><span class="sxs-lookup"><span data-stu-id="80e7d-105">Arguments</span></span>  
  
|<span data-ttu-id="80e7d-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="80e7d-106">Term</span></span>|<span data-ttu-id="80e7d-107">定義</span><span class="sxs-lookup"><span data-stu-id="80e7d-107">Definition</span></span>|  
|---|---|  
|`fileName`|<span data-ttu-id="80e7d-108">自訂資訊清單檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="80e7d-108">The path of the custom manifest file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80e7d-109">備註</span><span class="sxs-lookup"><span data-stu-id="80e7d-109">Remarks</span></span>  
 <span data-ttu-id="80e7d-110">根據預設，Visual Basic 編譯器會將內嵌指定 asInvoker 要求的執行層級的應用程式資訊清單。</span><span class="sxs-lookup"><span data-stu-id="80e7d-110">By default, the Visual Basic compiler embeds an application manifest that specifies a requested execution level of asInvoker.</span></span> <span data-ttu-id="80e7d-111">它會建立資訊清單中的可執行檔建置完成後，通常當您使用 Visual Studio 的 bin\Debug 或 bin\Release 資料夾的相同資料夾中。</span><span class="sxs-lookup"><span data-stu-id="80e7d-111">It creates the manifest in the same folder in which the executable file is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="80e7d-112">如果您想要提供自訂資訊清單，例如若要指定要求的執行層級 highestAvailable 或 requireAdministrator，使用此選項以指定的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="80e7d-112">If you want to supply a custom manifest, for example to specify a requested execution level of highestAvailable or requireAdministrator, use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80e7d-113">此選項和[/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)是互斥的選項。</span><span class="sxs-lookup"><span data-stu-id="80e7d-113">This option and the [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) option are mutually exclusive.</span></span> <span data-ttu-id="80e7d-114">如果您嘗試在相同的命令列中使用這兩個選項，就會發生建置錯誤。</span><span class="sxs-lookup"><span data-stu-id="80e7d-114">If you try to use both options in the same command line, you will get a build error.</span></span>  
  
 <span data-ttu-id="80e7d-115">沒有資訊清單的任何應用程式的應用程式指定要求的執行層級會受限於檔案及登錄虛擬化在 Windows Vista 中的使用者帳戶控制功能。</span><span class="sxs-lookup"><span data-stu-id="80e7d-115">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows Vista.</span></span> <span data-ttu-id="80e7d-116">如需虛擬化的詳細資訊，請參閱[Windows Vista 的 ClickOnce 部署](https://docs.microsoft.com/visualstudio/deployment/clickonce-deployment-on-windows-vista)。</span><span class="sxs-lookup"><span data-stu-id="80e7d-116">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](https://docs.microsoft.com/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="80e7d-117">如果下列條件時，您的應用程式會受制於虛擬化︰</span><span class="sxs-lookup"><span data-stu-id="80e7d-117">Your application will be subject to virtualization if either of the following conditions is true:</span></span>  
  
1.  <span data-ttu-id="80e7d-118">您使用`/nowin32manifest`選項，且未提供的資訊清單中的更新版本的建置步驟或做為 Windows 資源 (.res) 檔案的一部分使用`/win32resource`選項。</span><span class="sxs-lookup"><span data-stu-id="80e7d-118">You use the `/nowin32manifest` option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the `/win32resource` option.</span></span>  
  
2.  <span data-ttu-id="80e7d-119">您提供不會指定要求的執行層級的自訂資訊清單。</span><span class="sxs-lookup"><span data-stu-id="80e7d-119">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]<span data-ttu-id="80e7d-120">建立預設.manifest 檔案，並將它儲存在與可執行檔在一起的偵錯和發行目錄中。</span><span class="sxs-lookup"><span data-stu-id="80e7d-120"> creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="80e7d-121">您可以檢視或編輯預設資訊清單檔案，請按一下**檢視 UAC 設定**上**應用程式**專案設計工具中的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="80e7d-121">You can view or edit the default app.manifest file by clicking **View UAC Settings** on the **Application** tab in the Project Designer.</span></span> <span data-ttu-id="80e7d-122">如需詳細資訊，請參閱[應用程式] 頁面上，[專案設計工具 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="80e7d-122">For more information, see [Application Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="80e7d-123">您可以藉由提供應用程式資訊清單做為自訂的建置後步驟或 Win32 資源檔的`/nowin32manifest`選項。</span><span class="sxs-lookup"><span data-stu-id="80e7d-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the `/nowin32manifest` option.</span></span> <span data-ttu-id="80e7d-124">如果您想受制於 Windows Vista 上的檔案或登錄虛擬化您的應用程式，請使用該相同的選項。</span><span class="sxs-lookup"><span data-stu-id="80e7d-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="80e7d-125">這會防止編譯器建立和內嵌在 PE 檔中的預設資訊清單。</span><span class="sxs-lookup"><span data-stu-id="80e7d-125">This will prevent the compiler from creating and embedding a default manifest in the PE file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80e7d-126">範例</span><span class="sxs-lookup"><span data-stu-id="80e7d-126">Example</span></span>  
 <span data-ttu-id="80e7d-127">下列範例會顯示 Visual Basic 編譯器插入 PE 預設資訊清單。</span><span class="sxs-lookup"><span data-stu-id="80e7d-127">The following example shows the default manifest that the Visual Basic compiler inserts into a PE.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80e7d-128">編譯器會插入 XML 資訊清單中的標準應用程式名稱 MyApplication.app。</span><span class="sxs-lookup"><span data-stu-id="80e7d-128">The compiler inserts a standard application name MyApplication.app into the manifest XML.</span></span> <span data-ttu-id="80e7d-129">這是因應措施，讓 Windows Server 2003 Service Pack 3 上執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="80e7d-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="80e7d-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80e7d-130">See Also</span></span>  
 <span data-ttu-id="80e7d-131">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="80e7d-131">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="80e7d-132"> [/nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)</span><span class="sxs-lookup"><span data-stu-id="80e7d-132"> [/nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)</span></span>
