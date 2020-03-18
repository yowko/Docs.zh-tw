---
title: 依賴項載入 - .NET 核心
description: .NET Core 中的託管和非託管依賴項載入概述
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.topic: overview
ms.openlocfilehash: f6b5fc1f92171b61dcab162b782ca7212c602d76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "73416673"
---
# <a name="dependency-loading-in-net-core"></a>.NET 核心中的依賴項載入

每個 .NET 核心應用程式都有依賴關係。 即使是簡單的`hello world`應用程式也依賴于 .NET Core 類庫的某些部分。

瞭解 .NET 核心預設程式集載入邏輯有助於瞭解和調試典型的部署問題。

在某些應用程式中，依賴項在運行時動態確定。 在這些情況下，瞭解託管程式集和非託管依賴項的載入方式至關重要。

## <a name="understanding-assemblyloadcontext"></a>了解 AssemblyLoadContext

API<xref:System.Runtime.Loader.AssemblyLoadContext>是 .NET 核心載入設計的核心。 ["瞭解程式集載入上下文"](understanding-assemblyloadcontext.md)一文提供了設計的概念概述。

## <a name="loading-details"></a>載入詳細資料

載入演算法詳細資訊在以下幾篇文章中簡要介紹：

- [託管程式集載入演算法](loading-managed.md)
- [衛星程式集載入演算法](loading-resources.md)
- [非託管（本機）庫載入演算法](loading-unmanaged.md)
- [預設探測](default-probing.md)

## <a name="create-a-net-core-application-with-plugins"></a>建立具有外掛程式的 .NET Core 應用程式

本教程[使用外掛程式創建 .NET Core 應用程式](../tutorials/creating-app-with-plugin-support.md)介紹如何創建自訂程式集 LoadCoNtext。 它使用<xref:System.Runtime.Loader.AssemblyDependencyResolver>解析外掛程式的依賴項。 本教程將外掛程式的依賴項與託管應用程式正確隔離。

## <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>如何使用 .NET Core 中的組件卸載功能及對其進行偵錯

在 .NET Core 文章中的["如何使用和偵錯工具集可卸載性](../../standard/assembly/unloadability.md)"是一個分步教程。 它演示如何載入 .NET Core 應用程式，執行，然後卸載它。 本文還提供調試提示。
