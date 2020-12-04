---
title: 在 LCD 上顯示文字
description: 瞭解如何使用 .NET IoT 程式庫在液晶顯示器上顯示字元。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: d4c3e373207e23877903491871f4d09e11000c1a
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96586665"
---
<!--markdownlint-disable DOCSMD011 -->
# <a name="display-text-on-an-lcd"></a>在 LCD 上顯示文字

LCD 字元顯示適用于顯示資訊，而不需要外部監視器。 一般的 LCD 字元顯示可以直接連接至 GPIO 針腳，但這種方法需要使用最多10個 GPIO pin。 對於需要連接到裝置組合的案例，專很多的 GPIO 標頭到字元顯示通常不切實際。

許多製造商會使用整合 GPIO 擴充器來銷售 20x4 LCD 字元顯示器。 字元顯示會直接連接到 GPIO 展開器，然後透過 Inter-Integrated 電路 (I2C) 序列通訊協定連接到 Raspberry Pi。

在本主題中，您將使用 [.NET]，以使用 I2C GPIO 擴充程式來顯示 LCD 字元顯示器上的文字。

## <a name="prerequisites"></a>先決條件

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- [使用 I2C 介面 20X4 LCD 字元顯示](https://www.bing.com/images/search?q=20x4+lcd+display+with+i2c)<span class="docon docon-navigate-external x-hidden-focus"></span>
- 跳線
- 麵包板 (選用/建議) 
- Raspberry Pi GPIO (選用/建議) 
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

> [!NOTE]
> 有許多製造商的 LCD 字元顯示器。 大部分的設計都是一樣的，製造商也不應該與功能產生任何差異。 本教學課程是以「 [SUNFOUNDER LCD2004](https://www.sunfounder.com/lcd2004-module.html) 」進行參考 <span class="docon docon-navigate-external x-hidden-focus"></span> 。

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="prepare-the-hardware"></a>準備硬體

使用跳線來將 I2C GPIO 擴充器上的四個圖釘連接至 Raspberry Pi，如下所示：

- GND 至地面
- 與5V 的 VCC
- SDA 至 SDA (GPIO 2) 
- SCL 至 SCL (GPIO 3) 

如有需要，請參閱下列資料：

| I2C 介面 (顯示) 的背面 | Raspberry Pi GPIO |
|---------------------------------|-------------------|
| :::image type="content" source="../media/character-display-i2c-thumb.png" alt-text="顯示 I2C GPIO 展開器之字元顯示背面的影像。" lightbox="../media/character-display-i2c.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="顯示 Raspberry Pi GPIO 標頭背面的圖表。Raspberry Pi Foundation 的圖像。" lightbox="../media/gpio-pinout-diagram.png":::<br />[Raspberry Pi Foundation 的圖像](https://www.raspberrypi.org/documentation/usage/gpio/) <span class="docon docon-navigate-external x-hidden-focus"></span> 。
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a>建立應用程式

請在您慣用的開發環境中完成下列步驟：

1. 使用 [.NET CLI](../../core/tools/dotnet-new.md) 或 [Visual Studio](../../core/tutorials/with-visual-studio.md)建立新的 .net 主控台應用程式。 將它命名為 *LcdTutorial*。

    ```dotnetcli
    dotnet new console -o LcdTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. 使用下列程式碼取代 *Program.cs* 的內容：

    :::code language="csharp" source="~/iot-samples/tutorials/LcdTutorial/Program.cs" :::

    在上述程式碼中：

    - [Using](../../csharp/whats-new/csharp-8.md#using-declarations)宣告會藉 `I2cDevice` 由呼叫 `I2cDevice.Create` 並傳入 `I2cConnectionSettings` 具有 `busId` 和參數的新，來建立的實例 `deviceAddress` 。 這 `I2cDevice` 代表 I2C 匯流排。 宣告 `using` 可確保物件已處置，且硬體資源已正確釋放。

        > [!WARNING]
        > GPIO 擴充器的裝置位址取決於製造商使用的晶片。 具有 PCF8574 的 GPIO 展開器會使用該位址 `0x27` ，而使用 PCF8574A 晶片的則使用該位址 `0x3F` 。 請參閱您的 LCD 檔。

    - 另一個宣告會 `using` 建立的實例 `Pcf8574` ，並將傳遞至函式 `I2cDevice` 。 此實例代表 GPIO 展開器。
    - 另一個宣告會 `using` 建立的實例 `Lcd2004` ，以代表顯示。 會將數個參數傳遞給描述要用來與 GPIO 展開器通訊的設定的函式。 GPIO 擴充項會以參數形式傳遞 `controller` 。
    - `while`迴圈會無限期地執行。 每個反復專案：
        1. 清除顯示。
        1. 將游標位置設定為目前行上的第一個位置。
        1. 將目前的時間寫入目前游標位置的顯示位置。
        1. 反覆運算目前的行計數器。
        1. 睡眠 1000 ms。

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. 切換至部署目錄並執行可執行檔，以在 Raspberry Pi 上執行應用程式。

    ```bash
    ./LcdTutorial
    ```

    觀察每一行顯示的 LCD 字元顯示是否為目前的時間。

    > [!TIP]
    > 如果顯示器燈亮，但您沒有看到任何文字，請嘗試調整顯示器背面的對比撥號。

1. 按 <kbd>Ctrl + C</kbd>來終止程式。

恭喜！ 您已在 LCD 上使用 I2C 和 GPIO 擴充程式顯示文字！

## <a name="get-the-source-code"></a>取得原始程式碼

本教學課程的來源 [可在 GitHub 上](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/LcdTutorial)取得 <span class="docon docon-navigate-external x-hidden-focus"></span> 。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [瞭解如何使用一般用途的輸入/輸出來閃爍 LED](../tutorials/blink-led.md)
