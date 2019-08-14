---
title: .NET 中的 COM Interop
description: 了解如何在 .NET 中與 COM 程式庫交互操作。
author: jkoritzinsky
ms.author: jekoritz
ms.date: 07/11/2019
ms.openlocfilehash: 03ede2fc95f4114a4d80423bd7de2e46012a2431
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631422"
---
# <a name="com-interop-in-net"></a>.NET 中的 COM Interop

元件物件模型 (COM) 可讓物件向其他元件公開其功能並在 Windows 平台上主控應用程式。 為了協助使用者與現有的程式碼基底交互操作，.NET Framework 一律提供對於與 COM 程式庫交互操作的強大支援。 在 .NET Core 3.0 中，這項支援的一大部分已新增至 Windows 上的 .NET Core。 這裡的文件將說明常見的 COM Interop 技術如何運作，以及如何利用它們來與現有的 COM 程式庫交互操作。

- [COM 包裝函式](./com-wrappers.md)
- [COM 可呼叫包裝函式](./com-callable-wrapper.md)
- [執行階段可呼叫的包裝函式](./runtime-callable-wrapper.md)
- [限定 COM 交互操作的 .NET 型別](./qualify-net-types-for-interoperation.md)
