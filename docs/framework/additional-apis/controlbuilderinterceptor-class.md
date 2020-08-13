---
title: ControlBuilderInterceptor 類別
ms.date: 08/11/2020
api_name:
- System.Web.Compilation.ControlBuilderInterceptor
api_location:
- System.Web.dll
api_type:
- Assembly
topic_type:
- apiref
ms.openlocfilehash: 0cd7409deb9cb84783cfa70600999fa4b2a2d2e2
ms.sourcegitcommit: d337df55f83325918cbbd095eb573400bea49064
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2020
ms.locfileid: "88187987"
---
# <a name="controlbuilderinterceptor-class"></a><span data-ttu-id="f0ca8-102">ControlBuilderInterceptor 類別</span><span class="sxs-lookup"><span data-stu-id="f0ca8-102">ControlBuilderInterceptor class</span></span>

<span data-ttu-id="f0ca8-103">`ControlBuilderInterceptor`類別可讓您自訂或控制編譯進程。</span><span class="sxs-lookup"><span data-stu-id="f0ca8-103">The `ControlBuilderInterceptor` class allows the compilation process to be customized or controlled.</span></span>

## <a name="syntax"></a><span data-ttu-id="f0ca8-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f0ca8-104">Syntax</span></span>

```csharp
internal class ControlBuilderInterceptor
```

> [!WARNING]
> <span data-ttu-id="f0ca8-105">`ControlBuilderInterceptor`類別是內部的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="f0ca8-105">The `ControlBuilderInterceptor` class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="f0ca8-106">如「備註」一節所述，您可以檢查此類型是否存在，以判斷是否有攔截器類型支援。</span><span class="sxs-lookup"><span data-stu-id="f0ca8-106">As described in the Remarks section, the existence of this type can be checked to determine whether interceptor type support is present.</span></span> <span data-ttu-id="f0ca8-107">在任何情況下，Microsoft 不支援在實際執行應用程式中使用此類別。</span><span class="sxs-lookup"><span data-stu-id="f0ca8-107">Microsoft does not support any other use of this class in a production application under any circumstance.</span></span>

## <a name="remarks"></a><span data-ttu-id="f0ca8-108">備註</span><span class="sxs-lookup"><span data-stu-id="f0ca8-108">Remarks</span></span>

<span data-ttu-id="f0ca8-109">在 .NET Framework 2.0 和 .NET Framework 3.5 中， [8 月 2020](https://portal.msrc.microsoft.com/security-guidance/releasenotedetail/2020-Aug) 更新新增了使用攔截器類型來自訂或控制編譯器的支援。</span><span class="sxs-lookup"><span data-stu-id="f0ca8-109">In .NET Framework 2.0 and .NET Framework 3.5, the [August 2020](https://portal.msrc.microsoft.com/security-guidance/releasenotedetail/2020-Aug) updates added support for using an interceptor type to customize or control the compilation process.</span></span> <span data-ttu-id="f0ca8-110"><xref:System.Type.GetType?displayProperty=nameWithType>如下列程式碼所示，您可以使用來檢查此支援是否存在，以判斷該類型是否存在 `ControlBuilderInterceptor` 。</span><span class="sxs-lookup"><span data-stu-id="f0ca8-110">You can determine whether this support is present by using <xref:System.Type.GetType?displayProperty=nameWithType> to check the existence of the `ControlBuilderInterceptor` type, as demonstrated in the following code.</span></span>

```csharp
Type type = Type.GetType("System.Web.Compilation.ControlBuilderInterceptor, System.Web, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a");
```

<span data-ttu-id="f0ca8-111">如果傳回值為非 null，則會有攔截器支援。</span><span class="sxs-lookup"><span data-stu-id="f0ca8-111">If the return value is non-null, then interceptor support is present.</span></span> <span data-ttu-id="f0ca8-112">如果傳回值為 `null` ，或擲回例外狀況，則不會安裝2020年8月的更新，而且不會有攔截器支援。</span><span class="sxs-lookup"><span data-stu-id="f0ca8-112">If the return value is `null`, or if an exception is thrown, then the August 2020 updates have not been installed, and interceptor support is absent.</span></span>

<span data-ttu-id="f0ca8-113">如果有攔截器支援，您可以撰寫並註冊與編譯器互動的攔截器型別，其方式與更新版本 .NET Framework 的方法完全相同 <xref:System.Web.Compilation.ControlBuilderInterceptor> 。</span><span class="sxs-lookup"><span data-stu-id="f0ca8-113">If interceptor support is present, you can write and register an interceptor type that will interact with the compilation process in exactly the same way that <xref:System.Web.Compilation.ControlBuilderInterceptor> does on later versions of .NET Framework.</span></span> <span data-ttu-id="f0ca8-114">在 .NET Framework 2.0 和 .NET Framework 3.5 中，攔截器類型可以是符合下列需求的任何類別：</span><span class="sxs-lookup"><span data-stu-id="f0ca8-114">In .NET Framework 2.0 and .NET Framework 3.5, the interceptor type can be any class that meets the following requirements:</span></span>

* <span data-ttu-id="f0ca8-115">具有公用的無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="f0ca8-115">Has a public, parameterless constructor.</span></span>
* <span data-ttu-id="f0ca8-116">具有名為的公用、非靜態方法， `PreControlBuilderInit` `OnProcessGeneratedCode` 其具有與和方法相同的簽章和語義 <xref:System.Web.Compilation.ControlBuilderInterceptor.PreControlBuilderInit(System.Web.UI.ControlBuilder,System.Web.UI.TemplateParser,System.Web.UI.ControlBuilder,System.Type,System.String,System.String,System.Collections.IDictionary,System.Collections.IDictionary)> <xref:System.Web.Compilation.ControlBuilderInterceptor.OnProcessGeneratedCode(System.Web.UI.ControlBuilder,System.CodeDom.CodeCompileUnit,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeMemberMethod,System.CodeDom.CodeMemberMethod,System.Collections.IDictionary)> ，後者存在於較新的 .NET Framework 版本中。</span><span class="sxs-lookup"><span data-stu-id="f0ca8-116">Has public, non-static methods named `PreControlBuilderInit` and `OnProcessGeneratedCode` that have the same signature and semantics as the <xref:System.Web.Compilation.ControlBuilderInterceptor.PreControlBuilderInit(System.Web.UI.ControlBuilder,System.Web.UI.TemplateParser,System.Web.UI.ControlBuilder,System.Type,System.String,System.String,System.Collections.IDictionary,System.Collections.IDictionary)> and <xref:System.Web.Compilation.ControlBuilderInterceptor.OnProcessGeneratedCode(System.Web.UI.ControlBuilder,System.CodeDom.CodeCompileUnit,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeMemberMethod,System.CodeDom.CodeMemberMethod,System.Collections.IDictionary)> methods, which exist in later versions of .NET Framework.</span></span>

<span data-ttu-id="f0ca8-117">使用 `aspnet:20ControlBuilderInterceptor` ASP.NET 應用程式設定 () 中的金鑰，註冊攔截器類型 `<appSettings>` 。</span><span class="sxs-lookup"><span data-stu-id="f0ca8-117">Register the interceptor type by using the `aspnet:20ControlBuilderInterceptor` key in ASP.NET application settings (`<appSettings>`).</span></span> <span data-ttu-id="f0ca8-118">此應用程式設定必須列在您的電腦或應用程式 *web.config* 檔中。</span><span class="sxs-lookup"><span data-stu-id="f0ca8-118">This application setting must be listed in your computer or application *web.config* file.</span></span> <span data-ttu-id="f0ca8-119">使用元件限定的型別名稱來指定攔截器型別。</span><span class="sxs-lookup"><span data-stu-id="f0ca8-119">Specify the interceptor type by using its assembly-qualified type name.</span></span> <span data-ttu-id="f0ca8-120">下列範例顯示如何註冊名為的攔截器型別 `Fabrikam.Interceptor` 。</span><span class="sxs-lookup"><span data-stu-id="f0ca8-120">The following example shows how to register an interceptor type named `Fabrikam.Interceptor`.</span></span>

```xml
<configuration>
  ...
  <appSettings>
    ...
    <add key="aspnet:20ControlBuilderInterceptor"
         value="Fabrikam.Interceptor, Fabrikam, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2b3831f2f2b744f7" />
  </appSettings>
</configuration>
```

<span data-ttu-id="f0ca8-121">若要取得類型的元件限定名稱，請使用 <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> 屬性，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="f0ca8-121">To retrieve the assembly-qualified name of a type, use the <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> property, as demonstrated in the following code.</span></span>

```csharp
string assemblyQualifiedName = typeof(Fabrikam.Interceptor).AssemblyQualifiedName;
```

<span data-ttu-id="f0ca8-122">當攔截器支援存在時，編譯器會以上述方式與列出的類型互動。</span><span class="sxs-lookup"><span data-stu-id="f0ca8-122">When interceptor support is present, the compilation process interacts with the listed type in the manner described above.</span></span> <span data-ttu-id="f0ca8-123">當攔截器支援不存在時，會忽略應用程式設定，而且不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="f0ca8-123">When interceptor support is absent, the application setting is ignored and has no effect.</span></span>

## <a name="requirements"></a><span data-ttu-id="f0ca8-124">規格需求</span><span class="sxs-lookup"><span data-stu-id="f0ca8-124">Requirements</span></span>

<span data-ttu-id="f0ca8-125">**命名空間：** System.web. 編譯</span><span class="sxs-lookup"><span data-stu-id="f0ca8-125">**Namespace:** System.Web.Compilation</span></span>

<span data-ttu-id="f0ca8-126">**元件：** System.Web.dll) 中的 system.web (</span><span class="sxs-lookup"><span data-stu-id="f0ca8-126">**Assembly:** System.Web (in System.Web.dll)</span></span>

<span data-ttu-id="f0ca8-127">**.NET Framework 版本：** 3.5、2。0</span><span class="sxs-lookup"><span data-stu-id="f0ca8-127">**.NET Framework versions:** 3.5, 2.0</span></span>
