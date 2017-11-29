---
title: "以 Windows 8 上的 .NET Framework 2.0 為目標平台"
description: "深入了解使用 F # 時，目標為舊版的.NET Framework。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 63989543-95c3-4ab7-81f3-3834a8b15010
ms.openlocfilehash: 2c0191267da5bee7b844c11cdee168ccfb3321c4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="targeting-older-versions-of-net"></a>以舊版 .NET 為目標

> [!NOTE]
這篇文章不是最新的 Visual Studio 中的最新狀態。  將會更新。

如果您嘗試將目標.NET Framework 2.0，3.0 或 3.5 F # 專案在 Windows 8.1 上安裝 Visual Studio 時，可能發生下列錯誤： 

```
This project requires the 2.0 F# runtime, but that runtime is not installed.
```

這個錯誤是已知會發生在下列條件的組合：


- 您在 Windows 8.1 上安裝 Visual Studio。
<br />

- 您未啟用.NET Framework 3.5，才能安裝 Visual Studio。
<br />

- 您專案的目標.NET Framework 2.0、 3.0 或 3.5。
<br />

當您安裝 Visual Studio 時，它會偵測已安裝的.NET Framework 版本，並安裝並啟用.NET Framework 3.5 時，才會安裝 F # 2.0 執行階段。


## <a name="resolving-the-error"></a>解決錯誤
若要解決這個錯誤，您可以任一目標較新版的.NET Framework 中，或者您可以啟用 Windows 8.1 上為.NET Framework 3.5，然後再安裝 F # 2.0 執行階段執行安裝程式的 Visual Studio 中以**修復**選項。


#### <a name="to-enable-the-net-framework-35-on-windows-81"></a>若要啟用 Windows 8.1 上為.NET Framework 3.5

1. 在**啟動**畫面上，開始輸入**控制台**。
<br />  當您輸入該名稱，**控制台**圖示會出現在**應用程式**標題。
<br />

2. 選擇**控制台**圖示，選擇**程式**圖示，然後選擇 **開啟或關閉 Windows 功能**連結。
<br />

3. 請確定**.NET Framework 3.5 （包括.NET 2.0 和 3.0）**核取方塊已選取，然後選擇**確定** 按鈕。
<br />  您不需要選取核取方塊，任何的子節點的.NET framework 的選擇性元件。
<br />  如果尚未，啟用.NET Framework 3.5。
<br />


#### <a name="to-install-the-f-20-runtime"></a>若要安裝 F # 2.0 執行階段

1. 在 控制台 中選擇**程式**連結，，然後選擇 **程式和功能**連結。
<br />

2. 在已安裝的程式清單中，選擇的版本，您已安裝，然後選擇 [Visual Studio**變更**] 按鈕。
<br />

3. 安裝程式啟動之後，請選擇**修復** 按鈕。
<br />  如需詳細資訊，請參閱[安裝 Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)。
<br />
## <a name="see-also"></a>另請參閱
[Visual F#](../index.md)
