---
title: 相依性載入-.NET Core
description: .NET Core 中的 managed 和非受控相依性載入總覽
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.topic: overview
ms.openlocfilehash: 69cca28606c64479d500e731ba95fe404bea38df
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70234657"
---
# <a name="dependency-loading-in-net-core"></a>.NET Core 中的相依性載入

每個 .NET Core 應用程式都有相依性。 即使是簡單`hello world`的應用程式也會相依于 .net Core 類別庫的某些部分。

瞭解 .NET Core 預設元件載入邏輯有助於瞭解和偵測一般的部署問題。

在某些應用程式中, 相依性會在執行時間以動態方式決定。 在這些情況下, 請務必瞭解如何載入 managed 元件和非受控相依性。

## <a name="understanding-assemblyloadcontext"></a>了解 AssemblyLoadContext

<xref:System.Runtime.Loader.AssemblyLoadContext> API 是 .net Core 載入設計的核心。 [瞭解 AssemblyLoadCoNtext](understanding-assemblyloadcontext.md)一文提供設計的概念總覽。

## <a name="loading-details"></a>載入詳細資料

下列幾篇文章會簡要說明載入演算法的詳細資料:
- [Managed 元件載入演算法](loading-managed.md)
- [附屬元件載入演算法](loading-resources.md)
- [非受控 (原生) 程式庫載入演算法](loading-unmanaged.md)
- [預設探查](default-probing.md)

## <a name="create-a-net-core-application-with-plugins"></a>建立具有外掛程式的 .NET Core 應用程式

[使用外掛程式建立 .Net Core 應用程式](../tutorials/creating-app-with-plugin-support.md)教學課程說明如何建立自訂 AssemblyLoadCoNtext。 它會使用<xref:System.Runtime.Loader.AssemblyDependencyResolver>來解析外掛程式的相依性。 本教學課程會正確地隔離外掛程式與主控應用程式的相依性。

## <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>如何使用 .NET Core 中的組件卸載功能及對其進行偵錯

[如何在 .Net Core 中使用和 debug 元件卸載功能](../../standard/assembly/unloadability-howto.md)一文是逐步教學課程。 它會顯示如何載入 .NET Core 應用程式、執行, 然後將它卸載。 本文也提供調試秘訣。
