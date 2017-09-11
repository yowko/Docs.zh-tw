---
title: "-win32manifest (C# 編譯器選項) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /win32manifest
dev_langs:
- CSharp
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: Human Translation
ms.sourcegitcommit: bb28bf28c3d8a426322e1c1795941de7e9aa4bf6
ms.openlocfilehash: fd8c0a9a398c8f8d6c589ffcf0426a375a82a6a8
ms.contentlocale: zh-tw
ms.lasthandoff: 07/03/2017

---
# <a name="win32manifest-c-compiler-options"></a><span data-ttu-id="c8542-102">/win32manifest (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="c8542-102">/win32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="c8542-103">使用 **/win32manifest** 選項，指定要內嵌到專案的可攜式執行檔 (PE) 中的使用者定義 Win32 應用程式資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="c8542-103">Use the **/win32manifest** option to specify a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8542-104">語法</span><span class="sxs-lookup"><span data-stu-id="c8542-104">Syntax</span></span>  
  
```console  
/win32manifest: filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="c8542-105">引數</span><span class="sxs-lookup"><span data-stu-id="c8542-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="c8542-106">自訂資訊清單檔案的名稱和位置。</span><span class="sxs-lookup"><span data-stu-id="c8542-106">The name and location of the custom manifest file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8542-107">備註</span><span class="sxs-lookup"><span data-stu-id="c8542-107">Remarks</span></span>  
 <span data-ttu-id="c8542-108">根據預設，[!INCLUDE[csharp_current_short](~/includes/csharp-current-short-md.md)] 編譯器會內嵌應用程式資訊清單，以指定所要求之執行層級的 "asInvoker"。</span><span class="sxs-lookup"><span data-stu-id="c8542-108">By default, the [!INCLUDE[csharp_current_short](~/includes/csharp-current-short-md.md)] compiler embeds an application manifest that specifies a requested execution level of "asInvoker."</span></span> <span data-ttu-id="c8542-109">編譯器會在建置可執行檔所在的資料夾中建立資訊清單，當您使用 Visual Studio 時，通常會是 bin\Debug 或是 bin\Release 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c8542-109">It creates the manifest in the same folder in which the executable is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="c8542-110">如果您要提供自訂資訊清單，例如指定 "highestAvailable" 或 "requireAdministrator" 做為要求的執行層級，請使用此選項指定檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="c8542-110">If you want to supply a custom manifest, for example to specify a requested execution level of "highestAvailable" or "requireAdministrator," use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8542-111">此選項與 [/win32res (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) 選項互斥。</span><span class="sxs-lookup"><span data-stu-id="c8542-111">This option and the [/win32res (C# Compiler Options)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) option are mutually exclusive.</span></span> <span data-ttu-id="c8542-112">如果您嘗試在相同的命令列中使用這兩個選項，則會收到建置錯誤。</span><span class="sxs-lookup"><span data-stu-id="c8542-112">If you try to use both options in the same command line you will get a build error.</span></span>  
  
 <span data-ttu-id="c8542-113">如果應用程式的應用程式資訊清單未指定要求的執行層級，則會受限於 Windows Vista 中「使用者帳戶控制」功能下的檔案/登錄虛擬化。</span><span class="sxs-lookup"><span data-stu-id="c8542-113">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows Vista.</span></span> <span data-ttu-id="c8542-114">如需虛擬化的詳細資訊，請參閱 [The Windows Vista Developer Story: Windows Vista Application Development Requirements for User Account Control (UAC)](http://go.microsoft.com/fwlink/?LinkId=95452)(Windows Vista 開發人員小故事：Windows Vista 應用程式開發的使用者帳戶控制 (UAC) 需求)。</span><span class="sxs-lookup"><span data-stu-id="c8542-114">For more information about virtualization, see [The Windows Vista Developer Story: Windows Vista Application Development Requirements for User Account Control (UAC)](http://go.microsoft.com/fwlink/?LinkId=95452).</span></span>  
  
 <span data-ttu-id="c8542-115">如果符合上述任一個條件，您的應用程式將會受限於虛擬化︰</span><span class="sxs-lookup"><span data-stu-id="c8542-115">Your application will be subject to virtualization if either of these conditions is true:</span></span>  
  
-   <span data-ttu-id="c8542-116">您可以使用 **/nowin32manifest** 選項，而且未提供後面建置步驟中的資訊清單，或未使用 **/win32res** 選項將資訊清單作為 Windows 資源 (.res) 檔案的一部分。</span><span class="sxs-lookup"><span data-stu-id="c8542-116">You use the **/nowin32manifest** option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the **/win32res** option.</span></span>  
  
-   <span data-ttu-id="c8542-117">您可以提供未指定所要求執行層級的自訂資訊清單。</span><span class="sxs-lookup"><span data-stu-id="c8542-117">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="c8542-118"> 會建立預設.manifest 檔案，並將它與可執行檔一起儲存在偵錯和發行目錄中。</span><span class="sxs-lookup"><span data-stu-id="c8542-118"> creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="c8542-119">您可以在任何文字編輯器中建立自訂資訊清單，然後將檔案新增至專案，來新增自訂資訊清單。</span><span class="sxs-lookup"><span data-stu-id="c8542-119">You can add a custom manifest by creating one in any text editor and then adding the file to the project.</span></span> <span data-ttu-id="c8542-120">或者，您可以使用滑鼠右鍵按一下方案總管中的 [專案] 圖示，並按一下 [新增項目]，然後按一下 [應用程式資訊清單檔案]。</span><span class="sxs-lookup"><span data-stu-id="c8542-120">Alternatively, you can right-click the **Project** icon in **Solution Explorer**, click **Add New Item**, and then click **Application Manifest File**.</span></span> <span data-ttu-id="c8542-121">新增全新或現有資訊清單檔案之後，它將會顯示在 [資訊清單] 下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="c8542-121">After you have added your new or existing manifest file, it will appear in the **Manifest** drop down list.</span></span> <span data-ttu-id="c8542-122">如需詳細資訊，請參閱[專案設計工具、應用程式頁面 (C#)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-csharp)。</span><span class="sxs-lookup"><span data-stu-id="c8542-122">For more information, see [Application Page, Project Designer (C#)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="c8542-123">您可以使用 [/nowin32manifest (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) 選項，提供應用程式資訊清單作為自訂建置後步驟或 Win32 資源檔的一部分。</span><span class="sxs-lookup"><span data-stu-id="c8542-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the [/nowin32manifest (C# Compiler Options)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) option.</span></span> <span data-ttu-id="c8542-124">如果您想要應用程式受制於 Windows Vista 上的檔案或登錄虛擬化，請使用這個相同的選項。</span><span class="sxs-lookup"><span data-stu-id="c8542-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="c8542-125">這會防止編譯器在可攜式執行檔 (PE) 中建立和內嵌預設資訊清單。</span><span class="sxs-lookup"><span data-stu-id="c8542-125">This will prevent the compiler from creating and embedding a default manifest in the portable executable (PE) file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8542-126">範例</span><span class="sxs-lookup"><span data-stu-id="c8542-126">Example</span></span>  
 <span data-ttu-id="c8542-127">下列範例顯示 Visual C# 編譯器插入至 PE 的預設資訊清單。</span><span class="sxs-lookup"><span data-stu-id="c8542-127">The following example shows the default manifest that the Visual C# compiler inserts into a PE.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8542-128">編譯器會將標準應用程式名稱 " MyApplication.app " 插入至 xml。</span><span class="sxs-lookup"><span data-stu-id="c8542-128">The compiler inserts a standard application name " MyApplication.app " into the xml.</span></span> <span data-ttu-id="c8542-129">這是讓應用程式在 Windows Server 2003 Service Pack 3 上執行的因應措施。</span><span class="sxs-lookup"><span data-stu-id="c8542-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c8542-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8542-130">See Also</span></span>  
 <span data-ttu-id="c8542-131">[C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="c8542-131">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 <span data-ttu-id="c8542-132">[/nowin32manifest (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="c8542-132">[/nowin32manifest (C# Compiler Options)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) </span></span>  
 [<span data-ttu-id="c8542-133">NIB 如何：修改專案屬性和組態設定</span><span class="sxs-lookup"><span data-stu-id="c8542-133">NIB How to: Modify Project Properties and Configuration Settings</span></span>](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
