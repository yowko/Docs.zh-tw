---
title: 未受管理的程式庫載入演算法-.NET Core
description: .NET Core 中非受控元件載入演算法的詳細資料描述
ms.date: 10/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: c651aa6e0f37a968e6f8b26d1909def6fa488ccd
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250039"
---
# <a name="unmanaged-native-library-loading-algorithm"></a>非受控（原生）程式庫載入演算法

未受管理的程式庫會以包含各種階段的演算法找出並載入。

下列演算法說明如何透過 `PInvoke` 載入原生程式庫。

## <a name="pinvoke-load-library-algorithm"></a>`PInvoke` 載入程式庫演算法

當嘗試載入非受控元件時，`PInvoke` 會使用下列演算法：

1. 判斷 `active` <xref:System.Runtime.Loader.AssemblyLoadContext>。 若為非受控載入程式庫，則 `active` AssemblyLoadCoNtext 是元件中定義 `PInvoke` 的一個。

2. 若為 `active` <xref:System.Runtime.Loader.AssemblyLoadContext>，請嘗試依下列順序尋找元件：
    * 正在檢查其快取。

    * 呼叫 <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> 函數所設定的目前 @no__t 0 委派。

    * 在 `active` AssemblyLoadCoNtext 上呼叫 <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> 函數。

    * 檢查 @no__t 0 實例的快取，並執行[非受控（原生）程式庫探查](default-probing.md#unmanaged-native-library-probing)邏輯。

    * 引發 `active` AssemblyLoadCoNtext 的 <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> 事件。
