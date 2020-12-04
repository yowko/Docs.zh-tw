---
title: 從類比到數位轉換器讀取值
description: 瞭解如何使用類比轉數位轉換器來讀取可變電壓值。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: eda6d8980d256c8063f2bfe1e051b0cb90b587ad
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96586668"
---
<!--markdownlint-disable DOCSMD011 -->
# <a name="read-values-from-an-analog-to-digital-converter"></a>從類比到數位轉換器讀取值

類比轉數位轉換器 (ADC) 是可讀取類比輸入電壓值並將其轉換為數字值的裝置。 Adc 可用來從 thermistors、potentiometers 和其他裝置讀取值，這些裝置會根據特定條件變更阻力。

在本主題中，您將使用 .NET 在使用 potentiometer lambert 輸入電壓時，從 ADC 讀取值。

## <a name="prerequisites"></a>先決條件

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- [MCP3008](https://www.microchip.com/wwwproducts/MCP3008) <span class="docon docon-navigate-external x-hidden-focus"></span> 類比轉數位轉換器
- 三個 pin potentiometer
- 試驗電路板
- 跳線
- Raspberry Pi GPIO (選用/建議) 
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [prepare-pi-spi](../includes/prepare-pi-spi.md)]

## <a name="prepare-the-hardware"></a>準備硬體

使用硬體元件來建立線路，如下圖所示：

:::image type="content" source="../media/rpi-trimpot_spi-thumb.png" alt-text="Fritzing 圖顯示具有 MCP3008 ADC 和 potentiometer 的電路" lightbox="../media/rpi-trimpot_spi.png":::

MCP3008 使用串列周邊介面 (SPI) 來進行通訊。 以下是從 MCP3008 到 Raspberry Pi 和 potentiometer 的連接：

- V<sub>DD</sub> 至 3.3 v (以紅色) 顯示
- 3.3 V (red) 的 v<sub>參考</sub>
- AGND 至地面 (黑色) 
- CLK 至 SCLK (橙色) 
- D<sub>MISO</sub> (橙色) 
- MOSI (橙色<sub>的</sub> D) 
- CS/SHDN 至 CE0 (綠色) 
- DGND 至地面 (黑色) 
- 在 potentiometer 上 CH0 至變數 (中間) 釘選 (黃色) 

提供 3.3 V 和地面給 potentiometer 上的外部針腳。 順序並不重要。

視需要參閱下列引出線圖：

| MCP3008  | Raspberry Pi GPIO |
|----------|-------------------|
| :::image type="content" source="../media/mcp3008-diagram-thumb.png" alt-text="顯示 MCP3008 針腳的圖表" lightbox="../media/mcp3008-diagram.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="顯示 Raspberry Pi GPIO 標頭背面的圖表。Raspberry Pi Foundation 的圖像。" lightbox="../media/gpio-pinout-diagram.png":::<br />[Raspberry Pi Foundation 的圖像](https://www.raspberrypi.org/documentation/usage/gpio/)。
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a>建立應用程式

請在您慣用的開發環境中完成下列步驟：

1. 使用 [.NET CLI](../../core/tools/dotnet-new.md) 或 [Visual Studio](../../core/tutorials/with-visual-studio.md)建立新的 .net 主控台應用程式。 將它命名為 *AdcTutorial*。

    ```dotnetcli
    dotnet new console -o AdcTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. 使用下列程式碼取代 *Program.cs* 的內容：

    :::code language="csharp" source="~/iot-samples/tutorials/AdcTutorial/Program.cs" :::

    在上述程式碼中：

    - `hardwareSpiSettings` 設定為的新實例 `SpiConnectionSettings` 。 此函數會將 `busId` 參數設定為0，並將 `chipSelectLine` 參數設定為0。
    - [Using](../../csharp/whats-new/csharp-8.md#using-declarations)宣告會藉 `SpiDevice` 由呼叫和傳入來建立的實例 `SpiDevice.Create` `hardwareSpiSettings` 。 這 `SpiDevice` 代表 SPI 匯流排。 宣告 `using` 可確保物件已處置，且硬體資源已正確釋放。
    - 另一個宣告會 `using` 建立的實例 `Mcp3008` ，並將傳遞至函式 `SpiDevice` 。
    - `while`迴圈會無限期地執行。 每個反復專案：
        1. 藉由呼叫，讀取 ADC 上的 CH0 值 `mcp.Read(0)` 。
        1. 將值除以10.24。 MCP3008 是10位的 ADC，這表示它會傳回1024個可能的值，範圍是0-1023。 將值除以10.24 表示以百分比表示值。
        1. 將值四捨五入為最接近的整數。
        1. 將值寫入主控台的格式（以百分比表示）。
        1. 睡眠 500 ms。

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. 切換至部署目錄並執行可執行檔，以在 Raspberry Pi 上執行應用程式。

    ```bash
    ./AdcTutorial
    ```

    當您旋轉 potentiometer 撥號時，請觀察輸出。 這是因為 potentiometer 會將在 ADC 上提供給 CH0 的電壓改變。 ADC 會比較 CH0 上的輸入電壓與提供給 V<sub>REF</sub> 的參考電壓來產生值。

1. 按 <kbd>Ctrl + C</kbd>來終止程式。

恭喜！ 您已使用 SPI 從類比轉數位轉換器中讀取值。

## <a name="get-the-source-code"></a>取得原始程式碼

本教學課程的來源 [可在 GitHub 上](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/AdcTutorial)取得。 <span class="docon docon-navigate-external x-hidden-focus"></span>

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [瞭解如何使用一般用途的輸入/輸出來閃爍 LED](../tutorials/blink-led.md)
