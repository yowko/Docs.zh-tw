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
# <a name="unmanaged-native-library-loading-algorithm"></a><span data-ttu-id="2e1c7-103">非受控 (原生) 程式庫載入演算法</span><span class="sxs-lookup"><span data-stu-id="2e1c7-103">Unmanaged (native) library loading algorithm</span></span>

<span data-ttu-id="2e1c7-104">未受管理的程式庫會以包含各種階段的演算法找出並載入。</span><span class="sxs-lookup"><span data-stu-id="2e1c7-104">Unmanaged libraries are located and loaded with an algorithm involving various stages.</span></span>

<span data-ttu-id="2e1c7-105">下列演算法說明如何透過`PInvoke`載入原生程式庫。</span><span class="sxs-lookup"><span data-stu-id="2e1c7-105">The following algorithm describes how native libraries are loaded through `PInvoke`.</span></span>

## <a name="pinvoke-load-library-algorithm"></a><span data-ttu-id="2e1c7-106">`PInvoke`載入程式庫演算法</span><span class="sxs-lookup"><span data-stu-id="2e1c7-106">`PInvoke` load library algorithm</span></span>

<span data-ttu-id="2e1c7-107">`PInvoke`嘗試載入非受控元件時, 會使用下列演算法:</span><span class="sxs-lookup"><span data-stu-id="2e1c7-107">`PInvoke` uses the following algorithm when attempting to load an unmanaged assembly:</span></span>

1. <span data-ttu-id="2e1c7-108">`active`判斷。<xref:System.Runtime.Loader.AssemblyLoadContext></span><span class="sxs-lookup"><span data-stu-id="2e1c7-108">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="2e1c7-109">若為非受控載入程式庫`active` , 則 AssemblyLoadCoNtext 是的呼叫`PInvoke`者。</span><span class="sxs-lookup"><span data-stu-id="2e1c7-109">For an unmanaged load library, the `active` AssemblyLoadContext is the caller of the `PInvoke`.</span></span>

2. <span data-ttu-id="2e1c7-110">`active` 針對,請嘗試依<xref:System.Runtime.Loader.AssemblyLoadContext>下列順序尋找元件:</span><span class="sxs-lookup"><span data-stu-id="2e1c7-110">For the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, try to find the assembly in priority order by:</span></span>
    * <span data-ttu-id="2e1c7-111">正在檢查其快取。</span><span class="sxs-lookup"><span data-stu-id="2e1c7-111">Checking its cache.</span></span>

    * <span data-ttu-id="2e1c7-112">呼叫<xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType>函數所<xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType>設定的目前委派。</span><span class="sxs-lookup"><span data-stu-id="2e1c7-112">Calling the current <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> delegate set by the <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> function.</span></span>

    * <span data-ttu-id="2e1c7-113"><xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType>呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="2e1c7-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> function.</span></span>

    * <span data-ttu-id="2e1c7-114">檢查實例的快取, 並執行[非受控 (原生) 程式庫探查邏輯。](default-probing.md#unmanaged-native-library-probing) <xref:System.AppDomain></span><span class="sxs-lookup"><span data-stu-id="2e1c7-114">Checking the <xref:System.AppDomain> instance's cache and running the [Unmanaged (native) library probing](default-probing.md#unmanaged-native-library-probing) logic.</span></span>

    * <span data-ttu-id="2e1c7-115">引發AssemblyLoadCoNtext`active`的事件。 <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="2e1c7-115">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> event for the `active` AssemblyLoadContext.</span></span>

3. <span data-ttu-id="2e1c7-116">如果是新載入的非受控程式庫<xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> , 則會引發事件。</span><span class="sxs-lookup"><span data-stu-id="2e1c7-116">If the unmanaged library is newly loaded, the <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> event is raised.</span></span>
