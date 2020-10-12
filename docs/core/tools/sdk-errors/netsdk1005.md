---
title: NETSDK1005 和 NETSDK1047：資產檔案遺失目標
description: 如何解決資產檔案遺失目標的問題。
author: sfoslund
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1005
- NETSDK1047
ms.openlocfilehash: 6c22fd8c79c2ac6e024b46b4f67e08011d42efc6
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957140"
---
# <a name="netsdk1005-and-netsdk1047-asset-file-is-missing-target"></a>NETSDK1005 和 NETSDK1047：資產檔案遺失目標

本文**適用于：** ✔️ .NET 2.1.100 SDK 和更新版本

當 .NET SDK 發出錯誤 NETSDK1005 或 NETSDK1047 時，專案的資產檔案就會遺失其中一個目標 framework 的相關資訊。 通常可以藉由確保執行還原，而遺漏的目標值包含在專案的屬性中，來修正此問題 `TargetFrameworks` 。

> [!NOTE]
> 當 .NET 5 preview 8 的早期版本搭配使用時，有一個已知的問題，就是與導致此錯誤的 Visual Studio 16.8 預覽版本搭配使用。 具體而言，如果遺漏的目標是 `net5.0-windows7.0` 或 `net5.0` ，請確定您已更新為最新版本的 Visual Studio 和 .NET 5 SDK。
