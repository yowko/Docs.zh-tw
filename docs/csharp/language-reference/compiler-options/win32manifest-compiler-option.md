---
title: "-win32manifest (C# 編譯器選項)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /win32manifest
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 36a16f1ee037a1379399c7ee2e2c67427eb9d1b2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="-win32manifest-c-compiler-options"></a>-win32manifest (C# 編譯器選項)
使用 **-win32manifest** 選項，指定要內嵌到專案之可攜式執行檔 (PE) 中的使用者定義 Win32 應用程式資訊清單檔。  
  
## <a name="syntax"></a>語法  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a>引數  
 `filename`  
 自訂資訊清單檔案的名稱和位置。  
  
## <a name="remarks"></a>備註  
 根據預設，[!INCLUDE[csharp_current_short](~/includes/csharp-current-short-md.md)] 編譯器會內嵌應用程式資訊清單，以指定所要求之執行層級的 "asInvoker"。 編譯器會在建置可執行檔所在的資料夾中建立資訊清單，當您使用 Visual Studio 時，通常會是 bin\Debug 或是 bin\Release 資料夾。 如果您要提供自訂資訊清單，例如指定 "highestAvailable" 或 "requireAdministrator" 做為要求的執行層級，請使用此選項指定檔案名稱。  
  
> [!NOTE]
>  此選項與 [-win32res (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) 選項互斥。 如果您嘗試在相同的命令列中使用這兩個選項，則會收到建置錯誤。  
  
 如果應用程式的應用程式資訊清單未指定要求的執行層級，則會受限於 Windows 中「使用者帳戶控制」功能下的檔案/登錄虛擬化。 如需詳細資訊，請參閱[使用者帳戶控制](/windows/access-protection/user-account-control/user-account-control-overview)。  
  
 如果符合上述任一個條件，您的應用程式將會受限於虛擬化︰  
  
-   您可以使用 **-nowin32manifest** 選項，而且未提供後面建置步驟中的資訊清單，或未使用 **-win32res** 選項將資訊清單作為 Windows 資源 (.res) 檔案的一部分。  
  
-   您可以提供未指定所要求執行層級的自訂資訊清單。  
  
 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 會建立預設.manifest 檔案，並將它與可執行檔一起儲存在偵錯和發行目錄中。 您可以在任何文字編輯器中建立自訂資訊清單，然後將檔案新增至專案，來新增自訂資訊清單。 或者，您可以使用滑鼠右鍵按一下方案總管中的 [專案] 圖示，並按一下 [新增項目]，然後按一下 [應用程式資訊清單檔案]。 新增全新或現有資訊清單檔案之後，它將會顯示在 [資訊清單] 下拉式清單中。 如需詳細資訊，請參閱[專案設計工具、應用程式頁面 (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp)。  
  
 您可以使用 [-nowin32manifest (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) 選項，提供應用程式資訊清單作為自訂建置後步驟或 Win32 資源檔的一部分。 如果您想要應用程式受制於 Windows Vista 上的檔案或登錄虛擬化，請使用這個相同的選項。 這會防止編譯器在可攜式執行檔 (PE) 中建立和內嵌預設資訊清單。  
  
## <a name="example"></a>範例  
 下列範例顯示 Visual C# 編譯器插入至 PE 的預設資訊清單。  
  
> [!NOTE]
>  編譯器會將標準應用程式名稱 " MyApplication.app " 插入至 xml。 這是讓應用程式在 Windows Server 2003 Service Pack 3 上執行的因應措施。  
  
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
  
## <a name="see-also"></a>請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)  
 [-nowin32manifest (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)  
 [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
