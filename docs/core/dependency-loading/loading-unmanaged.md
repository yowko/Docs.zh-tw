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
# <a name="unmanaged-native-library-loading-algorithm"></a><span data-ttu-id="13f8b-103">非受控（原生）程式庫載入演算法</span><span class="sxs-lookup"><span data-stu-id="13f8b-103">Unmanaged (native) library loading algorithm</span></span>

<span data-ttu-id="13f8b-104">未受管理的程式庫會以包含各種階段的演算法找出並載入。</span><span class="sxs-lookup"><span data-stu-id="13f8b-104">Unmanaged libraries are located and loaded with an algorithm involving various stages.</span></span>

<span data-ttu-id="13f8b-105">下列演算法說明如何透過 `PInvoke` 載入原生程式庫。</span><span class="sxs-lookup"><span data-stu-id="13f8b-105">The following algorithm describes how native libraries are loaded through `PInvoke`.</span></span>

## <a name="pinvoke-load-library-algorithm"></a><span data-ttu-id="13f8b-106">`PInvoke` 載入程式庫演算法</span><span class="sxs-lookup"><span data-stu-id="13f8b-106">`PInvoke` load library algorithm</span></span>

<span data-ttu-id="13f8b-107">當嘗試載入非受控元件時，`PInvoke` 會使用下列演算法：</span><span class="sxs-lookup"><span data-stu-id="13f8b-107">`PInvoke` uses the following algorithm when attempting to load an unmanaged assembly:</span></span>

1. <span data-ttu-id="13f8b-108">判斷 `active` <xref:System.Runtime.Loader.AssemblyLoadContext>。</span><span class="sxs-lookup"><span data-stu-id="13f8b-108">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="13f8b-109">若為非受控載入程式庫，則 `active` AssemblyLoadCoNtext 是元件中定義 `PInvoke` 的一個。</span><span class="sxs-lookup"><span data-stu-id="13f8b-109">For an unmanaged load library, the `active` AssemblyLoadContext is the one with the assembly that defines the `PInvoke`.</span></span>

2. <span data-ttu-id="13f8b-110">若為 `active` <xref:System.Runtime.Loader.AssemblyLoadContext>，請嘗試依下列順序尋找元件：</span><span class="sxs-lookup"><span data-stu-id="13f8b-110">For the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, try to find the assembly in priority order by:</span></span>
    * <span data-ttu-id="13f8b-111">正在檢查其快取。</span><span class="sxs-lookup"><span data-stu-id="13f8b-111">Checking its cache.</span></span>

    * <span data-ttu-id="13f8b-112">呼叫 <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> 函數所設定的目前 @no__t 0 委派。</span><span class="sxs-lookup"><span data-stu-id="13f8b-112">Calling the current <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> delegate set by the <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> function.</span></span>

    * <span data-ttu-id="13f8b-113">在 `active` AssemblyLoadCoNtext 上呼叫 <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> 函數。</span><span class="sxs-lookup"><span data-stu-id="13f8b-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> function on the `active` AssemblyLoadContext.</span></span>

    * <span data-ttu-id="13f8b-114">檢查 @no__t 0 實例的快取，並執行[非受控（原生）程式庫探查](default-probing.md#unmanaged-native-library-probing)邏輯。</span><span class="sxs-lookup"><span data-stu-id="13f8b-114">Checking the <xref:System.AppDomain> instance's cache and running the [Unmanaged (native) library probing](default-probing.md#unmanaged-native-library-probing) logic.</span></span>

    * <span data-ttu-id="13f8b-115">引發 `active` AssemblyLoadCoNtext 的 <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> 事件。</span><span class="sxs-lookup"><span data-stu-id="13f8b-115">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> event for the `active` AssemblyLoadContext.</span></span>
