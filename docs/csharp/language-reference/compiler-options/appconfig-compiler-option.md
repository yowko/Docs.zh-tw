---
title: "-appconfig (C# 編譯器選項)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /appconfig
helpviewer_keywords: /appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ca752c6264d0ee886aa4c248738097e0caf1d756
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="appconfig-c-compiler-options"></a><span data-ttu-id="c9678-102">/appconfig (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="c9678-102">/appconfig (C# Compiler Options)</span></span>
<span data-ttu-id="c9678-103">**/appconfig** 編譯器選項可讓 C# 應用程式將組件應用程式組態檔 (app.config) 的位置指定到組件繫結時間的 Common Language Runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="c9678-103">The **/appconfig** compiler option enables a C# application to specify the location of an assembly's application configuration (app.config) file to the common language runtime (CLR) at assembly binding time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9678-104">語法</span><span class="sxs-lookup"><span data-stu-id="c9678-104">Syntax</span></span>  
  
```console  
/appconfig:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="c9678-105">引數</span><span class="sxs-lookup"><span data-stu-id="c9678-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="c9678-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="c9678-106">Required.</span></span> <span data-ttu-id="c9678-107">包含組件繫結設定的應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="c9678-107">The application configuration file that contains assembly binding settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9678-108">備註</span><span class="sxs-lookup"><span data-stu-id="c9678-108">Remarks</span></span>  
 <span data-ttu-id="c9678-109">**/appconfig** 的其中一種用法就是進階案例；在此案例中，組件必須同時參考特定參考組件的 .NET Framework 版本以及 .NET Framework for Silverlight 版本。</span><span class="sxs-lookup"><span data-stu-id="c9678-109">One use of **/appconfig** is advanced scenarios in which an assembly has to reference both the .NET Framework version and the .NET Framework for Silverlight version of a particular reference assembly at the same time.</span></span> <span data-ttu-id="c9678-110">例如，以 Windows Presentation Foundation (WPF) 撰寫的 XAML 設計工具，可能必須同時參考 WPF Desktop (設計工具的使用者介面) 和 Silverlight 所附的 WPF 子集。</span><span class="sxs-lookup"><span data-stu-id="c9678-110">For example, a XAML designer written in Windows Presentation Foundation (WPF) might have to reference both the WPF Desktop, for the designer's user interface, and the subset of WPF that is included with Silverlight.</span></span> <span data-ttu-id="c9678-111">相同的設計工具組件必須存取這兩個組件。</span><span class="sxs-lookup"><span data-stu-id="c9678-111">The same designer assembly has to access both assemblies.</span></span> <span data-ttu-id="c9678-112">根據預設，不同的參考會導致編譯器錯誤，因為組件繫結關係會將兩個組件視為對等項目。</span><span class="sxs-lookup"><span data-stu-id="c9678-112">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span>  
  
 <span data-ttu-id="c9678-113">**/appconfig** 編譯器選項可讓您使用 `<supportPortability>` 標記指定停用預設行為的 app.config 檔案位置，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="c9678-113">The **/appconfig** compiler option enables you to specify the location of an app.config file that disables the default behavior by using a `<supportPortability>` tag, as shown in the following example.</span></span>  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 <span data-ttu-id="c9678-114">編譯器會將檔案位置傳遞至 CLR 的組件繫結關係邏輯。</span><span class="sxs-lookup"><span data-stu-id="c9678-114">The compiler passes the location of the file to the CLR's assembly-binding logic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c9678-115">如果使用 Microsoft Build Engine (MSBuild) 來建置應用程式，您可以將屬性標記新增至 .csproj 檔案，以設定 **/appconfig** 編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="c9678-115">If you are using the Microsoft Build Engine (MSBuild) to build your application, you can set the **/appconfig** compiler option by adding a property tag to the .csproj file.</span></span> <span data-ttu-id="c9678-116">若要使用專案中已設定的 app.config 檔案，請將屬性標記 `<UseAppConfigForCompiler>` 新增至 .csproj 檔案，並將其值設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="c9678-116">To use the app.config file that is already set in the project, add property tag `<UseAppConfigForCompiler>` to the .csproj file and set its value to `true`.</span></span> <span data-ttu-id="c9678-117">若要指定不同的 app.config 檔案，請新增屬性標記 `<AppConfigForCompiler>` 並將其值設定為檔案位置。</span><span class="sxs-lookup"><span data-stu-id="c9678-117">To specify a different app.config file, add property tag `<AppConfigForCompiler>` and set its value to the location of the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9678-118">範例</span><span class="sxs-lookup"><span data-stu-id="c9678-118">Example</span></span>  
 <span data-ttu-id="c9678-119">下例示範的 app.config 檔案，可讓應用程式同時參考存在於兩個實作中之任何 .NET Framework 組件的 .NET Framework 實作和 .NET Framework for Silverlight 實作。</span><span class="sxs-lookup"><span data-stu-id="c9678-119">The following example shows an app.config file that enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="c9678-120">**/appconfig** 編譯器選項會指定此 app.config 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="c9678-120">The **/appconfig** compiler option specifies the location of this app.config file.</span></span>  
  
```xml  
<configuration>  
      <runtime>  
      <assemblyBinding>  
            <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
            <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
      </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9678-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9678-121">See Also</span></span>  
 [<span data-ttu-id="c9678-122">\<supportPortability > 項目</span><span class="sxs-lookup"><span data-stu-id="c9678-122">\<supportPortability> Element</span></span>](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)  
 [<span data-ttu-id="c9678-123">依字母順序列出 C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="c9678-123">C# Compiler Options Listed Alphabetically</span></span>](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)
