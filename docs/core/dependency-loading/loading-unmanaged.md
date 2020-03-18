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
# <a name="unmanaged-native-library-loading-algorithm"></a><span data-ttu-id="ef7e4-103">非託管（本機）庫載入演算法</span><span class="sxs-lookup"><span data-stu-id="ef7e4-103">Unmanaged (native) library loading algorithm</span></span>

<span data-ttu-id="ef7e4-104">非託管庫位於並載入了涉及不同階段的演算法。</span><span class="sxs-lookup"><span data-stu-id="ef7e4-104">Unmanaged libraries are located and loaded with an algorithm involving various stages.</span></span>

<span data-ttu-id="ef7e4-105">以下演算法描述本機庫如何通過`PInvoke`載入 方式。</span><span class="sxs-lookup"><span data-stu-id="ef7e4-105">The following algorithm describes how native libraries are loaded through `PInvoke`.</span></span>

## <a name="pinvoke-load-library-algorithm"></a><span data-ttu-id="ef7e4-106">`PInvoke`負載庫演算法</span><span class="sxs-lookup"><span data-stu-id="ef7e4-106">`PInvoke` load library algorithm</span></span>

<span data-ttu-id="ef7e4-107">`PInvoke`嘗試載入非託管程式集時使用以下演算法：</span><span class="sxs-lookup"><span data-stu-id="ef7e4-107">`PInvoke` uses the following algorithm when attempting to load an unmanaged assembly:</span></span>

1. <span data-ttu-id="ef7e4-108">確定`active`<xref:System.Runtime.Loader.AssemblyLoadContext>。</span><span class="sxs-lookup"><span data-stu-id="ef7e4-108">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="ef7e4-109">對於非託管負載庫，`active`程式集 LoadCoNtext 是具有定義 的`PInvoke`程式集的。</span><span class="sxs-lookup"><span data-stu-id="ef7e4-109">For an unmanaged load library, the `active` AssemblyLoadContext is the one with the assembly that defines the `PInvoke`.</span></span>

2. <span data-ttu-id="ef7e4-110">對於`active`<xref:System.Runtime.Loader.AssemblyLoadContext>， 請嘗試按優先順序順序查找程式集：</span><span class="sxs-lookup"><span data-stu-id="ef7e4-110">For the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, try to find the assembly in priority order by:</span></span>
    * <span data-ttu-id="ef7e4-111">檢查其緩存。</span><span class="sxs-lookup"><span data-stu-id="ef7e4-111">Checking its cache.</span></span>

    * <span data-ttu-id="ef7e4-112">按<xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType>函式呼叫<xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType>當前委託集。</span><span class="sxs-lookup"><span data-stu-id="ef7e4-112">Calling the current <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> delegate set by the <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> function.</span></span>

    * <span data-ttu-id="ef7e4-113">在<xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType>`active`程式集載入上下文上調用函數。</span><span class="sxs-lookup"><span data-stu-id="ef7e4-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> function on the `active` AssemblyLoadContext.</span></span>

    * <span data-ttu-id="ef7e4-114">檢查<xref:System.AppDomain>實例的緩存並運行[非託管（本機）庫探測](default-probing.md#unmanaged-native-library-probing)邏輯。</span><span class="sxs-lookup"><span data-stu-id="ef7e4-114">Checking the <xref:System.AppDomain> instance's cache and running the [Unmanaged (native) library probing](default-probing.md#unmanaged-native-library-probing) logic.</span></span>

    * <span data-ttu-id="ef7e4-115">引發<xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType>`active`程式集載入上下文的事件。</span><span class="sxs-lookup"><span data-stu-id="ef7e4-115">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> event for the `active` AssemblyLoadContext.</span></span>
