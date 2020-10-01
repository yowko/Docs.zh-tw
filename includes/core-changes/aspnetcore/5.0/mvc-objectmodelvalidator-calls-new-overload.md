---
ms.openlocfilehash: 5083403a24a4a695d6970ef9c7a006796f41a86b
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609290"
---
### <a name="mvc-objectmodelvalidator-calls-a-new-overload-of-validationvisitorvalidate"></a><span data-ttu-id="9fb06-101">MVC： ObjectModelValidator 呼叫 ValidationVisitor 的新多載。 Validate</span><span class="sxs-lookup"><span data-stu-id="9fb06-101">MVC: ObjectModelValidator calls a new overload of ValidationVisitor.Validate</span></span>

<span data-ttu-id="9fb06-102">在 ASP.NET Core 5.0 中，已加入的多載 <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="9fb06-102">In ASP.NET Core 5.0, an overload of the <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType> was added.</span></span> <span data-ttu-id="9fb06-103">新的多載會接受包含屬性的最上層模型實例：</span><span class="sxs-lookup"><span data-stu-id="9fb06-103">The new overload accepts the top-level model instance that contains properties:</span></span>

```diff
  bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel);
+ bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container);
```

<span data-ttu-id="9fb06-104"><xref:Microsoft.AspNetCore.Mvc.ModelBinding.ObjectModelValidator> 叫用這個新的多載 `ValidationVisitor` ，以執行驗證。</span><span class="sxs-lookup"><span data-stu-id="9fb06-104"><xref:Microsoft.AspNetCore.Mvc.ModelBinding.ObjectModelValidator> invokes this new overload of `ValidationVisitor` to perform validation.</span></span> <span data-ttu-id="9fb06-105">如果您的驗證程式庫與 ASP.NET Core MVC 的模型驗證系統整合，這個新的多載是相關的。</span><span class="sxs-lookup"><span data-stu-id="9fb06-105">This new overload is pertinent if your validation library integrates with ASP.NET Core MVC's model validation system.</span></span>

<span data-ttu-id="9fb06-106">如需相關討論，請參閱 GitHub issue [dotnet/aspnetcore # 26020](https://github.com/dotnet/aspnetcore/issues/26020)。</span><span class="sxs-lookup"><span data-stu-id="9fb06-106">For discussion, see GitHub issue [dotnet/aspnetcore#26020](https://github.com/dotnet/aspnetcore/issues/26020).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9fb06-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="9fb06-107">Version introduced</span></span>

<span data-ttu-id="9fb06-108">5.0</span><span class="sxs-lookup"><span data-stu-id="9fb06-108">5.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9fb06-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="9fb06-109">Old behavior</span></span>

<span data-ttu-id="9fb06-110">`ObjectModelValidator` 在模型驗證期間叫用下列多載：</span><span class="sxs-lookup"><span data-stu-id="9fb06-110">`ObjectModelValidator` invokes the following overload during model validation:</span></span>

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel)
```

#### <a name="new-behavior"></a><span data-ttu-id="9fb06-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="9fb06-111">New behavior</span></span>

<span data-ttu-id="9fb06-112">`ObjectModelValidator` 在模型驗證期間叫用下列多載：</span><span class="sxs-lookup"><span data-stu-id="9fb06-112">`ObjectModelValidator` invokes the following overload during model validation:</span></span>

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
```

#### <a name="reason-for-change"></a><span data-ttu-id="9fb06-113">變更的原因</span><span class="sxs-lookup"><span data-stu-id="9fb06-113">Reason for change</span></span>

<span data-ttu-id="9fb06-114">這項變更的推出是為了支援 <xref:System.ComponentModel.DataAnnotations.CompareAttribute> 依賴其他屬性檢查的驗證程式，例如。</span><span class="sxs-lookup"><span data-stu-id="9fb06-114">This change was introduced to support validators, such as <xref:System.ComponentModel.DataAnnotations.CompareAttribute>, that rely on inspection of other properties.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9fb06-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="9fb06-115">Recommended action</span></span>

<span data-ttu-id="9fb06-116">`ObjectModelValidator` `ValidationVisitor` 當以 .net 5.0 或更新版本為目標時，依賴叫用現有多載的驗證架構必須覆寫新的方法：</span><span class="sxs-lookup"><span data-stu-id="9fb06-116">Validation frameworks that rely on `ObjectModelValidator` to invoke the existing overload of `ValidationVisitor` must override the new method when targeting .NET 5.0 or later:</span></span>

```csharp
public class MyCustomValidationVisitor : ValidationVisitor
{
+  public override bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
+  {
+    ...
}
```

#### <a name="category"></a><span data-ttu-id="9fb06-117">類別</span><span class="sxs-lookup"><span data-stu-id="9fb06-117">Category</span></span>

<span data-ttu-id="9fb06-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9fb06-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9fb06-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="9fb06-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate`

-->
