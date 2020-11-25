---
title: NETSDK1073：無法辨識 FrameworkReference
description: 如何解決找不到 FrameworkReference 的問題。
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1073
ms.openlocfilehash: 2b2dbf2a0d3e13dca4fe634529b7951f2333ce28
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713024"
---
# <a name="netsdk1073-the-frameworkreference-was-not-recognized"></a>NETSDK1073：無法辨識 FrameworkReference

本文 **適用于：** ✔️ .net CORE 2.1.100 SDK 和更新版本

此錯誤通常表示 SDK 找不到特定的 FrameworkReference 版本。 請嘗試刪除您的 *obj* 和 *bin* 資料夾並執行， `dotnet restore` 以重新下載最新的目標套件。

或者，您的安裝可能有問題，因此請確定您是使用最新版本的 .NET 並 Visual Studio
