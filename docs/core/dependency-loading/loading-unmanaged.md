---
title: 非託管庫載入演算法 - .NET Core
description: .NET Core 中非託管程式集載入演算法的詳細資訊說明
ms.date: 10/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: c651aa6e0f37a968e6f8b26d1909def6fa488ccd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72250039"
---
# <a name="unmanaged-native-library-loading-algorithm"></a>非託管（本機）庫載入演算法

非託管庫位於並載入了涉及不同階段的演算法。

以下演算法描述本機庫如何通過`PInvoke`載入 方式。

## <a name="pinvoke-load-library-algorithm"></a>`PInvoke`負載庫演算法

`PInvoke`嘗試載入非託管程式集時使用以下演算法：

1. 確定`active`<xref:System.Runtime.Loader.AssemblyLoadContext>。 對於非託管負載庫，`active`程式集 LoadCoNtext 是具有定義 的`PInvoke`程式集的。

2. 對於`active`<xref:System.Runtime.Loader.AssemblyLoadContext>， 請嘗試按優先順序順序查找程式集：
    * 檢查其緩存。

    * 按<xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType>函式呼叫<xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType>當前委託集。

    * 在<xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType>`active`程式集載入上下文上調用函數。

    * 檢查<xref:System.AppDomain>實例的緩存並運行[非託管（本機）庫探測](default-probing.md#unmanaged-native-library-probing)邏輯。

    * 引發<xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType>`active`程式集載入上下文的事件。
