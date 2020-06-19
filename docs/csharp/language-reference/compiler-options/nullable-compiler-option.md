---
title: '-nullable （c # 編譯器選項）'
ms.date: 06/04/2020
f1_keywords:
- /nullable
helpviewer_keywords:
- nullable compiler option [C#]
- /nullable compiler option [C#]
- -nullable compiler option [C#]
ms.openlocfilehash: 7454bb316507c3aaea208094127552712421dff6
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990130"
---
# <a name="-nullable-c-compiler-options"></a>-nullable （c # 編譯器選項）

**-Nullable**選項可讓您指定所需的可為 null 內容。

## <a name="syntax"></a>語法

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a>引數

`+` &#124; `-`  
指定 `+` 或**可為 null**，會使編譯器啟用可為 null 的內容。 指定 `-` ，如果您未指定 **-nullable**，則會停用可為 null 的內容。

`enable`&#124; `disable` &#124; `warnings` &#124;`annotations`  
指定可為 null 的內容選項。 類似于 `+` 或 `-` ，可啟用和停用，但允許更細微的可為 null 內容的精確程度。 `enable`引數的作用與您指定 **-nullable**相同，會啟用可為 null 的內容。 指定 `disable` 將會停用可為 null 的內容。 提供 `warnings` 引數時，**可為 null：警告**，可為 null 警告內容已啟用。 當指定 `annotations` 引數時，**可為 null**的注釋內容已啟用。

## <a name="remarks"></a>備註

流程分析是用來推斷可執行程式碼中變數的 null 屬性。 變數的推斷 null 屬性與變數的宣告 null 屬性無關。 方法呼叫即使有條件地省略也會進行分析。 例如， <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 在發行模式中。

以下列屬性標注之方法的調用也會影響流程分析：

- 簡單的前置條件： <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> 和<xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute>
- 簡單的後置條件： <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> 和<xref:System.Diagnostics.CodeAnalysis.NotNullAttribute>
- 條件式後置條件： <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> 和<xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute>
- <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute>（例如， `DoesNotReturnIf(false)` 針對 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ）和<xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- 成員後置條件： <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> 和<xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])>

### <a name="to-set-this-compiler-option-in-a-project"></a>若要在專案中設定這個編譯器選項

編輯 *.csproj*檔案，在階層內新增 `<Nullable>` 標記 `Project/PropertyGroup` ：

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
