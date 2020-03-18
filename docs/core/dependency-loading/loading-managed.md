---
title: 託管程式集載入演算法 - .NET 核心
description: .NET Core 中託管程式集載入演算法的詳細資訊說明
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 312a320676be6eb453697e0704ab771a6707618b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "73973505"
---
# <a name="managed-assembly-loading-algorithm"></a>託管程式集載入演算法

託管程式集位於並載入了涉及不同階段的演算法。

除附屬程式集和`WinRT`程式集之外，所有託管程式集都使用相同的演算法。

## <a name="when-are-managed-assemblies-loaded"></a>何時載入託管程式集？

觸發託管程式集負載的最常見機制是靜態程式集引用。 每當代碼使用在另一個程式集中定義的類型時，編譯器都會插入這些引用。 這些程式集根據需要載入`load-by-name`（ ）。

直接使用特定 API 也會觸發負載：

|API  |描述  |`Active` <xref:System.Runtime.Loader.AssemblyLoadContext> |
|---------|---------|---------|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyName%2A?displayProperty=nameWithType>|`Load-by-name`|[此](../../csharp/language-reference/keywords/this.md)實例。|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType><p><xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromNativeImagePath%2A?displayProperty=nameWithType>|從路徑載入。|[此](../../csharp/language-reference/keywords/this.md)實例。|
<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromStream%2A?displayProperty=nameWithType>|從物件載入。|[此](../../csharp/language-reference/keywords/this.md)實例。|
|<xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>|從新<xref:System.Runtime.Loader.AssemblyLoadContext>實例中的路徑載入|新 <xref:System.Runtime.Loader.AssemblyLoadContext> 執行個體。|
<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>|從實例中的<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>路徑載入。<p>將<xref:System.Runtime.Loader.AssemblyLoadContext.Resolving>處理常式添加到<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>。 處理常式將從其目錄中載入程式集的依賴項。|<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> 執行個體。|
|<xref:System.Reflection.Assembly.Load(System.Reflection.AssemblyName)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.String)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>|`Load-by-name`.|從調用方推斷。<p>首選<xref:System.Runtime.Loader.AssemblyLoadContext>方法。|
|<xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.Byte[],System.Byte[])?displayProperty=nameWithType>|從新<xref:System.Runtime.Loader.AssemblyLoadContext>實例中的物件載入。|新 <xref:System.Runtime.Loader.AssemblyLoadContext> 執行個體。|
<xref:System.Type.GetType(System.String)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType>|`Load-by-name`.|從調用方推斷。<p>首選<xref:System.Type.GetType%2A?displayProperty=nameWithType>具有`assemblyResolver`參數的方法。|
<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>|如果類型`name`描述程式集限定泛型型別，則觸發`Load-by-name`。|從調用方推斷。<p>使用<xref:System.Type.GetType%2A?displayProperty=nameWithType>程式集限定類型名稱時，首選。|
<xref:System.Activator.CreateInstance(System.String,System.String)?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Object[])?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Boolean,System.Reflection.BindingFlags,System.Reflection.Binder,System.Object[],System.Globalization.CultureInfo,System.Object[])?displayProperty=nameWithType>|`Load-by-name`.|從調用方推斷。<p>更喜歡<xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>採用<xref:System.Type>參數的方法。|

## <a name="algorithm"></a>演算法

以下演算法描述運行時如何載入託管程式集。

1. 確定`active`<xref:System.Runtime.Loader.AssemblyLoadContext>。

    - 對於靜態程式集引用，`active`<xref:System.Runtime.Loader.AssemblyLoadContext>是載入引用程式集的實例。
    - 首選 API 使`active`<xref:System.Runtime.Loader.AssemblyLoadContext>顯式。
    - 其他 API 推斷`active`<xref:System.Runtime.Loader.AssemblyLoadContext>。 對於這些 API，將使用<xref:System.Runtime.Loader.AssemblyLoadContext.CurrentContextualReflectionContext?displayProperty=nameWithType>該屬性。 如果其值為`null`，則使用推斷<xref:System.Runtime.Loader.AssemblyLoadContext>實例。
    - 見上表。

2. 對於`Load-by-name`方法，活動<xref:System.Runtime.Loader.AssemblyLoadContext>載入程式集。 按優先順序順序排列：
    - 檢查其`cache-by-name`。

    - 調用函數<xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType>。

    - 檢查<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>實例的緩存並運行[託管程式集預設探測](default-probing.md#managed-assembly-default-probing)邏輯。

    - 引發活動<xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType>程式集載入上下文的事件。

    - 引發事件<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>。

3. 對於其他類型的負載，載入`active`<xref:System.Runtime.Loader.AssemblyLoadContext>元件。 按優先順序順序排列：
    - 檢查其`cache-by-name`。

    - 從指定的路徑或原始程式集物件載入。

4. 在這兩種情況下，如果新載入了程式集，則：
   - 便會引發 <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> 事件。
   - 引用將添加到程式集的<xref:System.Runtime.Loader.AssemblyLoadContext>實例 。 `cache-by-name`

5. 如果找到程式集，則根據需要`active`<xref:System.Runtime.Loader.AssemblyLoadContext>向實例的`cache-by-name`增加參考。
