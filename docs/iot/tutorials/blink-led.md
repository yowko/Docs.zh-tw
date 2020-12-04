---
title: 閃爍 LED
description: 瞭解如何使用 .NET IoT 程式庫來使 LED 閃爍。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: 07a050c0655f9cae3d7f2b924c0dd07ac1c6c0b9
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96586670"
---
# <a name="blink-an-led"></a>閃爍 LED

一般用途的 i/o (GPIO) pin 可以個別控制。 這適用于控制 Led、轉送和其他具狀態裝置。 在本主題中，您將使用 .NET 和 Raspberry Pi 的 GPIO 針腳來開啟 LED 並重複閃爍。

## <a name="prerequisites"></a>先決條件

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- 5 mm LED
- 330Ω電阻器
- 試驗電路板
- 跳線
- Raspberry Pi GPIO (選用/建議) 
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [ensure-ssh](../includes/ensure-ssh.md)]

## <a name="prepare-the-hardware"></a>準備硬體

使用硬體元件來建立線路，如下圖所示：

:::image type="content" source="../media/rpi-led_bb-thumb.png" alt-text="Fritzing 圖顯示具有 LED 和電阻的電路" lightbox="../media/rpi-led_bb.png":::

上圖描述下列連接：

- GPIO 18 到 LED 陽極 (更長、正面潛在客戶) 
- 領先的陰極 (更短、負面潛在客戶) 至330Ω電阻器 (可能會結束) 
- 330Ω電阻器 (其他端) 至地面

[!INCLUDE [tutorial-rpi-gpio](../includes/tutorial-rpi-gpio.md)]

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a>建立應用程式

請在您慣用的開發環境中完成下列步驟：

1. 使用 [.NET CLI](../../core/tools/dotnet-new.md) 或 [Visual Studio](../../core/tutorials/with-visual-studio.md)建立新的 .net 主控台應用程式。 將它命名為 *BlinkTutorial*。

    ```dotnetcli
    dotnet new console -o BlinkTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. 使用下列程式碼取代 *Program.cs* 的內容：

    :::code language="csharp" source="~/iot-samples/tutorials/BlinkTutorial/Program.cs" :::

    在上述程式碼中：

    - [Using](../../csharp/whats-new/csharp-8.md#using-declarations)宣告會建立的實例 `GpioController` 。 宣告 `using` 可確保物件已處置，且硬體資源已正確釋放。
    - 已開啟 GPIO pin 碼18作為輸出
    - `while`迴圈會無限期地執行。 每個反復專案：
        1. 將值寫入 GPIO 針腳18。 若 `ledOn` 為 true，則會 `PinValue.High` 在) 寫入 (。 否則，它會寫入 `PinValue.Low` 。
        1. 睡眠 1000 ms。
        1. 切換的值 `ledOn` 。

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. 切換至部署目錄並執行可執行檔，以在 Raspberry Pi 上執行應用程式。

    ```bash
    ./BlinkTutorial
    ```

    LED 會在每秒閃爍一次。

1. 按 <kbd>Ctrl + C</kbd>來終止程式。

恭喜！ 您已使用 GPIO 來使 LED 閃爍。

## <a name="get-the-source-code"></a>取得原始程式碼

本教學課程的來源 [可在 GitHub 上](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/BlinkTutorial)取得 <span class="docon docon-navigate-external x-hidden-focus"></span> 。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [瞭解如何從感應器讀取環境條件](../tutorials/temp-sensor.md)
