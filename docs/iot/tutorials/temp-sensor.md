---
title: 從感應器讀取環境情況
description: 瞭解如何使用 .NET IoT 程式庫來讀取 termperature、氣壓壓力和濕度。
author: camsoper
ms.author: casoper
ms.date: 11/14/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: 1270e7629e9afc12b1d76d260d4b8b51428f1040
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96586671"
---
# <a name="read-environmental-conditions-from-a-sensor"></a>從感應器讀取環境情況

IoT 裝置最常見的其中一個案例是偵測環境狀況。 有各種感應器可用來監視溫度、濕度、氣壓壓力等等。

在本主題中，您將使用 .NET 從感應器讀取環境條件。

## <a name="prerequisites"></a>先決條件

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- [BME280](https://learn.adafruit.com/adafruit-bme280-humidity-barometric-pressure-temperature-sensor-breakout) <span class="docon docon-navigate-external x-hidden-focus"></span> 濕度/氣壓壓力/溫度感應器分類
- 跳線
- 麵包板 (選用) 
- Raspberry Pi GPIO (選用) 
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

> [!IMPORTANT]
> 有許多 BME280 突破的製造商。 大部分的設計都很類似，而且製造商不應該與功能產生任何差異。 本教學課程會嘗試考慮變化。 確定您的 BME280 分類包含 (I2C) 介面的 Inter-Integrated 電路。

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="prepare-the-hardware"></a>準備硬體

使用硬體元件來建立線路，如下圖所示：

:::image type="content" source="../media/rpi-bmp280_i2c-thumb.png" alt-text="Fritzing 圖，顯示從 Raspberry Pi 到 BME280 排列面板的連接" lightbox="../media/rpi-bmp280_i2c.png":::

以下是從 Raspberry Pi 到 BME280 分組的連接：

- 3.3 v 至 VIN *或* 3V3 (以紅色) 顯示
- GND (黑) 的地面
- SDA (GPIO 2) 至 SDI *或* SDA (blue) 
- SCL (GPIO 3) 至 SCK *或* scl (橙色) 

[!INCLUDE [tutorial-rpi-gpio](../includes/tutorial-rpi-gpio.md)]

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a>建立應用程式

請在您慣用的開發環境中完成下列步驟：

1. 使用 [.NET CLI](../../core/tools/dotnet-new.md) 或 [Visual Studio](../../core/tutorials/with-visual-studio.md)建立新的 .net 主控台應用程式。 將它命名為 *SensorTutorial*。

    ```dotnetcli
    dotnet new console -o SensorTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. 使用下列程式碼取代 *Program.cs* 的內容：

    :::code language="csharp" source="~/iot-samples/tutorials/SensorTutorial/Program.cs" :::

    在上述程式碼中：

    - `i2cSettings` 設定為的新實例 `I2cConnectionSettings` 。 此函式會將 `busId` 參數設定為1，並將 `deviceAddress` 參數設定為 `Bme280.DefaultI2cAddress` 。

        > [!IMPORTANT]
        > 有些 BME280 的專題製造商會使用次要位址值。 針對這些裝置，請使用 `Bme280.SecondaryI2cAddress` 。

    - [Using](../../csharp/whats-new/csharp-8.md#using-declarations)宣告會藉 `I2cDevice` 由呼叫和傳入來建立的實例 `I2cDevice.Create` `i2cSettings` 。 這 `I2cDevice` 代表 I2C 匯流排。 宣告 `using` 可確保物件已處置，且硬體資源已正確釋放。
    - 另一個宣告會 `using` 建立的實例 `Bme280` ，以代表感應器。 `I2cDevice`會在函式中傳遞。
    - 藉由呼叫，可取得晶片使用晶片目前 (預設) 設定來測量的所需時間 `GetMeasurementDuration` 。
    - `while`迴圈會無限期地執行。 每個反復專案：
        1. 清除主控台。
        1. 將電源模式設定為 `Bmx280PowerMode.Forced` 。 這會強制晶片執行一項測量、儲存結果，然後進入睡眠狀態。
        1. 讀取溫度、壓力、濕度和高度的值。

            > [!NOTE]
            > 高度是由裝置系結計算。 這項使用的多載 `TryReadAltitude` 表示產生估計值的海洋級壓力。

        1. 將目前的環境條件寫入主控台。
        1. 睡眠 1000 ms。

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. 切換至部署目錄並執行可執行檔，以在 Raspberry Pi 上執行應用程式。

    ```bash
    ./SensorTutorial
    ```

    觀察主控台中的感應器輸出。

1. 按 <kbd>Ctrl + C</kbd>來終止程式。

恭喜！ 您已使用 I2C 來讀取溫度/濕度/氣壓壓力感應器的值！

## <a name="get-the-source-code"></a>取得原始程式碼

本教學課程的來源 [可在 GitHub 上](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/SensorTutorial)取得 <span class="docon docon-navigate-external x-hidden-focus"></span> 。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [瞭解如何在 LCD 上顯示文字](../tutorials/lcd-display.md)
