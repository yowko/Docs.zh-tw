---
title: 未受管理的程式庫載入演算法-.NET Core
description: .NET Core 中非受控元件載入演算法的詳細資料描述
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 8240cb730180637393e2545f8013d3f1439be719
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70234607"
---
# <a name="unmanaged-native-library-loading-algorithm"></a>非受控 (原生) 程式庫載入演算法

未受管理的程式庫會以包含各種階段的演算法找出並載入。

下列演算法說明如何透過`PInvoke`載入原生程式庫。

## <a name="pinvoke-load-library-algorithm"></a>`PInvoke`載入程式庫演算法

`PInvoke`嘗試載入非受控元件時, 會使用下列演算法:

1. `active`判斷。<xref:System.Runtime.Loader.AssemblyLoadContext> 若為非受控載入程式庫`active` , 則 AssemblyLoadCoNtext 是的呼叫`PInvoke`者。

2. `active` 針對,請嘗試依<xref:System.Runtime.Loader.AssemblyLoadContext>下列順序尋找元件:
    * 正在檢查其快取。

    * 呼叫<xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType>函數所<xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType>設定的目前委派。

    * <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType>呼叫函式。

    * 檢查實例的快取, 並執行[非受控 (原生) 程式庫探查邏輯。](default-probing.md#unmanaged-native-library-probing) <xref:System.AppDomain>

    * 引發AssemblyLoadCoNtext`active`的事件。 <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType>

3. 如果是新載入的非受控程式庫<xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> , 則會引發事件。
