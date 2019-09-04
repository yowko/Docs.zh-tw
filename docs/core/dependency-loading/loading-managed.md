---
title: Managed 元件載入演算法-.NET Core
description: .NET Core 中 managed 元件載入演算法的詳細資料描述
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: bf95cbd0eebed064f0198ae9b0f7a4288a938f8a
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70234630"
---
# <a name="managed-assembly-loading-algorithm"></a>Managed 元件載入演算法

受控元件會以包含各種階段的演算法來找出並載入。

除了附屬元件和`WinRT`元件以外的所有 managed 元件都使用相同的演算法。

## <a name="when-are-managed-assemblies-loaded"></a>載入 managed 元件的時間為何？

觸發 managed 元件載入最常見的機制是靜態元件參考。 每當程式碼使用另一個元件中所定義的型別時, 編譯器就會插入這些參考。 這些元件是執行時間`load-by-name`所需的載入 ()。

直接使用特定 Api 也會觸發負載:

|API  |描述  |`Active` <xref:System.Runtime.Loader.AssemblyLoadContext> |
|---------|---------|---------|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyName%2A?displayProperty=nameWithType>|`Load-by-name`|[這個](../../csharp/language-reference/keywords/this.md)實例。|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType><p><xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromNativeImagePath%2A?displayProperty=nameWithType>|從路徑載入。|[這個](../../csharp/language-reference/keywords/this.md)實例。|
<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromStream%2A?displayProperty=nameWithType>|從物件載入。|[這個](../../csharp/language-reference/keywords/this.md)實例。|
|<xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>|從新<xref:System.Runtime.Loader.AssemblyLoadContext>實例中的路徑載入|新 <xref:System.Runtime.Loader.AssemblyLoadContext> 執行個體。|
<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>|從<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>實例中的路徑載入。<p>將處理常式加入<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>至。 <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving> 處理常式會從其目錄載入元件的相依性。|<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> 執行個體。|
|<xref:System.Reflection.Assembly.Load(System.Reflection.AssemblyName)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.String)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>|`Load-by-name`.|從呼叫者推斷。<p>偏好<xref:System.Runtime.Loader.AssemblyLoadContext>方法。|
|<xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.Byte[],System.Byte[])?displayProperty=nameWithType>|從物件載入。|從呼叫者推斷。<p>偏好<xref:System.Runtime.Loader.AssemblyLoadContext>方法。|
<xref:System.Type.GetType(System.String)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType>|`Load-by-name`.|從呼叫者推斷。<p><xref:System.Type.GetType%2A?displayProperty=nameWithType> 偏好`assemblyResolver`使用具有引數的方法。|
<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>|如果類型`name`描述元件限定的泛型型別, 則觸發`Load-by-name`a。|從呼叫者推斷。<p>偏好<xref:System.Type.GetType%2A?displayProperty=nameWithType>使用元件限定的型別名稱時。|
<xref:System.Activator.CreateInstance(System.String,System.String)?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Object[])?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Boolean,System.Reflection.BindingFlags,System.Reflection.Binder,System.Object[],System.Globalization.CultureInfo,System.Object[])?displayProperty=nameWithType>|`Load-by-name`.|從呼叫者推斷。<p>偏好<xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>採用引數<xref:System.Type>的方法。|

## <a name="algorithm"></a>演算法

下列演算法描述執行時間如何載入 managed 元件。

1. `active`判斷。<xref:System.Runtime.Loader.AssemblyLoadContext>

    - 若是靜態元件參考, `active` <xref:System.Runtime.Loader.AssemblyLoadContext>則是載入參考元件的實例。
    - 慣用的 api 會`active`進行明確的<xref:System.Runtime.Loader.AssemblyLoadContext> 。
    - 其他 Api 會推斷`active`。 <xref:System.Runtime.Loader.AssemblyLoadContext> 針對這些 api, <xref:System.Runtime.Loader.AssemblyLoadContext.CurrentContextualReflectionContext?displayProperty=nameWithType>會使用屬性。 如果其值為`null`, 則會使用<xref:System.Runtime.Loader.AssemblyLoadContext>推斷的實例。
    - 請參閱上表。

2. 對於方法, 現用<xref:System.Runtime.Loader.AssemblyLoadContext>會載入元件。 `Load-by-name` 依優先順序排序依據:
    - 檢查其`cache-by-name`。

    - <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType>呼叫函式。

    - 檢查實例<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>的快取和執行[managed 元件預設探查](default-probing.md#managed-assembly-default-probing)邏輯。

    - 引發作用中 AssemblyLoadCoNtext 的事件。<xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType>

    - <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>引發事件。

3. 對於其他類型的載入, `active` <xref:System.Runtime.Loader.AssemblyLoadContext>會載入元件。 依優先順序排序依據:
    - 檢查其`cache-by-name`。

    - 從指定的路徑或原始元件物件載入。

4. 不論是哪一種情況, 如果剛載入元件, 則:
   - 便會引發 <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> 事件。
   - 參考會加入元件的<xref:System.Runtime.Loader.AssemblyLoadContext> `cache-by-name`實例中。

5. 如果找到元件, 則會視需要`active` <xref:System.Runtime.Loader.AssemblyLoadContext>將參考加入實例的`cache-by-name`。
