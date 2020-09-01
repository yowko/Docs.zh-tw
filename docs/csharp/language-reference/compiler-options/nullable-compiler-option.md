---
description: '-可為 null (c # 編譯器選項) '
title: '-可為 null (c # 編譯器選項) '
author: IEvangelist
ms.author: dapine
ms.date: 06/04/2020
f1_keywords:
- /nullable
helpviewer_keywords:
- nullable compiler option [C#]
- /nullable compiler option [C#]
- -nullable compiler option [C#]
ms.openlocfilehash: f9c6c204d2563865f741c6ddb4644eb56f956c12
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125042"
---
# <a name="-nullable-c-compiler-options"></a>-可為 null (c # 編譯器選項) 

**-可為 null**的選項可讓您指定所需的可為 null 內容。

## <a name="syntax"></a>語法

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a>引數

`+` &#124; `-`  
指定 `+` （或只是 **可為 null**）會導致編譯器啟用可為 null 的內容。 指定 `-` ，如果您未指定 **-可為 null**，則會停用可為 null 的內容。

`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`  
指定可為 null 的內容選項。 類似于 `+` 或 `-` ，表示要啟用和停用，但允許更多的可為 null 內容的精確程度。 `enable`引數的作用與您指定 **-nullable**的相同，可啟用可為 null 的內容。 指定 `disable` 將會停用可為 null 的內容。 提供 `warnings` 引數（ **可為 null：警告**）時，會啟用可為 null 的警告內容。 當指定 `annotations` 引數（ **-nullable：注釋**）時，可為 null 注釋內容已啟用。

## <a name="remarks"></a>備註

流程分析用來推斷可執行程式碼內變數的可 null 性。 變數的推斷 null 屬性與變數宣告的可 null 性無關。 即使有條件地省略方法呼叫，也會進行分析。 例如， <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 在發行模式中。

以下列屬性標注之方法的調用也會影響流程分析：

- 簡單的前置條件： <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> 和 <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute>
- 簡單的後置條件： <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> 和 <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute>
- 條件式後置條件： <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> 和 <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute>
- <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> 例如， (`DoesNotReturnIf(false)` <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>) 和 <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- 成員後置條件： <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> 和 <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])>

### <a name="to-set-this-compiler-option-in-a-project"></a>若要在專案中設定這個編譯器選項

編輯 *.csproj* 檔案，以在階層 `<Nullable>` 中新增標記 `Project/PropertyGroup` ：

```xml
<Project Sdk="...">

  <PropertyGroup>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## <a name="see-also"></a>另請參閱

- [C # 編譯器選項](./index.md)
- [可為 Null 的參考型別](../../nullable-references.md)
