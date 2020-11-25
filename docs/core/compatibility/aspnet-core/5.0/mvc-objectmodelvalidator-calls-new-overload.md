---
title: 重大變更： MVC： ObjectModelValidator 呼叫 ValidationVisitor 的新多載。 Validate
description: 瞭解 ASP.NET Core 5.0 的重大變更，標題為 MVC： ObjectModelValidator 呼叫 ValidationVisitor 的新多載。 Validate
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: b28c357f51291a4f73889d5d413a983f79e09daf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760782"
---
# <a name="mvc-objectmodelvalidator-calls-a-new-overload-of-validationvisitorvalidate"></a>MVC： ObjectModelValidator 呼叫 ValidationVisitor 的新多載。 Validate

在 ASP.NET Core 5.0 中，已加入的多載 <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType> 。 新的多載會接受包含屬性的最上層模型實例：

```diff
  bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel);
+ bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container);
```

<xref:Microsoft.AspNetCore.Mvc.ModelBinding.ObjectModelValidator> 叫用這個新的多載 `ValidationVisitor` ，以執行驗證。 如果您的驗證程式庫與 ASP.NET Core MVC 的模型驗證系統整合，這個新的多載是相關的。

如需相關討論，請參閱 GitHub issue [dotnet/aspnetcore # 26020](https://github.com/dotnet/aspnetcore/issues/26020)。

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="old-behavior"></a>舊的行為

`ObjectModelValidator` 在模型驗證期間叫用下列多載：

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel)
```

## <a name="new-behavior"></a>新的行為

`ObjectModelValidator` 在模型驗證期間叫用下列多載：

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
```

## <a name="reason-for-change"></a>變更的原因

這項變更的推出是為了支援 <xref:System.ComponentModel.DataAnnotations.CompareAttribute> 依賴其他屬性檢查的驗證程式，例如。

## <a name="recommended-action"></a>建議的動作

`ObjectModelValidator` `ValidationVisitor` 當以 .net 5.0 或更新版本為目標時，依賴叫用現有多載的驗證架構必須覆寫新的方法：

```csharp
public class MyCustomValidationVisitor : ValidationVisitor
{
+  public override bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
+  {
+    ...
}
```

## <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`Overload:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate`

-->
