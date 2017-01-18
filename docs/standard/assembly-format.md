---
title: ".NET 組件檔格式"
description: ".NET 組件檔格式"
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 6520323e-ff28-4c8a-ba80-e64a413199e6
translationtype: Human Translation
ms.sourcegitcommit: 30175813af95911c8ab4f2f0e39c40bed49a23b3
ms.openlocfilehash: e6212a63e74f2d1525e87480b092861be9f92379

---

# <a name="net-assembly-file-format"></a>.NET 組件檔格式

.NET 平台定義用來完整描述並包含 .NET 程式的二進位檔案格式 "assembly"。 組件用於程式本身以及任何相依的程式庫。 除了適當的 .NET 執行階段之外，.NET 程式也可以執行為一個或多個沒有其他必要成品的組件。 雖然有時會使用這種格式 (例如，WinRT) 進行描述，但是原生相依性 (包括作業系統 API) 會有不同的考量，而且不會包含在 .NET 組件格式內。

> 每個 CLI 元件都會攜帶該元件特定宣告、實作和參考的中繼資料。 因此，元件特定中繼資料是指元件中繼資料，而且產生的元件即為來自 ECMA 335 I.9.1 的自我描述元件和組件。

格式會完整指定並標準化為 ECMA 335。 所有 .NET 編譯器和執行階段都會使用這種格式。 所記載且不常更新之二進位格式的目前狀態已是互通性的主要優點 (即需求)。 這種格式上次在 2005 年進行重大更新 (.NET 2.0)，可容納泛型和處理器架構。

格式為 CPU 並且無作業系統無關。 它已用作將目標設為許多晶片和 CPU 的 .NET 執行階段一部分。 雖然格式本身具有 Windows 傳承，但是可在任何作業系統上實作。 作業系統互通性的最重大選擇就是大部分值都是以位元組由小到大格式儲存。 它沒有電腦指標大小 (例如，32 位元、64 位元) 的特定同質性。

.NET 組件格式對於指定的程式或程式庫結構也具有相當的描述性。 它會特別描述組件的內部元件︰定義的組件參考和類型，以及其內部結構。 工具或 API 可以讀取和處理這項資訊以供顯示，或進行程式設計決策。

## <a name="format"></a>格式

.NET 二進位格式是根據 Windows [PE 檔案](http://en.wikipedia.org/wiki/Portable_Executable)格式。 事實上，.NET 類別庫是一致的 Windows PE，並且顯示在第一次看到 Windows 動態連結程式庫 (DLL) 或應用程式執行檔 (EXE) 時。 這是 Windows 上極為實用的特性，在此，它們可以偽裝為原生可執行二進位檔，並進行一些相同的處理 (例如，OS 載入、PE 工具)。

![組件標頭](./media/assembly-format/assembly-headers.png)

來自 ECMA 335 II.25.1 的組件標頭 (執行階段檔案格式的結構)。

## <a name="processing-the-assemblies"></a>處理組件

可能會撰寫工具或 API 來處理組件。 組件資訊可在執行階段進行程式設計決策、重新撰寫組件、在編輯器中提供 API IntelliSense，以及產生文件。 [System.Reflection](https://msdn.microsoft.com/library/system.reflection.aspx) 和 [Mono.Cecil](http://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) 是常用於此目途之工具的不錯範例。



<!--HONumber=Nov16_HO3-->


