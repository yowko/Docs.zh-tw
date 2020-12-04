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
# <a name="read-values-from-an-analog-to-digital-converter"></a><span data-ttu-id="d4136-103">從類比到數位轉換器讀取值</span><span class="sxs-lookup"><span data-stu-id="d4136-103">Read values from an analog-to-digital converter</span></span>

<span data-ttu-id="d4136-104">類比轉數位轉換器 (ADC) 是可讀取類比輸入電壓值並將其轉換為數字值的裝置。</span><span class="sxs-lookup"><span data-stu-id="d4136-104">An analog-to-digital converter (ADC) is a device that can read an analog input voltage value and convert it into a digital value.</span></span> <span data-ttu-id="d4136-105">Adc 可用來從 thermistors、potentiometers 和其他裝置讀取值，這些裝置會根據特定條件變更阻力。</span><span class="sxs-lookup"><span data-stu-id="d4136-105">ADCs are used for reading values from thermistors, potentiometers, and other devices that change resistance based on certain conditions.</span></span>

<span data-ttu-id="d4136-106">在本主題中，您將使用 .NET 在使用 potentiometer lambert 輸入電壓時，從 ADC 讀取值。</span><span class="sxs-lookup"><span data-stu-id="d4136-106">In this topic, you will use .NET to read values from an ADC as you modulate the input voltage with a potentiometer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d4136-107">先決條件</span><span class="sxs-lookup"><span data-stu-id="d4136-107">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="d4136-108">[MCP3008](https://www.microchip.com/wwwproducts/MCP3008) <span class="docon docon-navigate-external x-hidden-focus"></span> 類比轉數位轉換器</span><span class="sxs-lookup"><span data-stu-id="d4136-108">[MCP3008](https://www.microchip.com/wwwproducts/MCP3008) <span class="docon docon-navigate-external x-hidden-focus"></span> analog-to-digital converter</span></span>
- <span data-ttu-id="d4136-109">三個 pin potentiometer</span><span class="sxs-lookup"><span data-stu-id="d4136-109">Three-pin potentiometer</span></span>
- <span data-ttu-id="d4136-110">試驗電路板</span><span class="sxs-lookup"><span data-stu-id="d4136-110">Breadboard</span></span>
- <span data-ttu-id="d4136-111">跳線</span><span class="sxs-lookup"><span data-stu-id="d4136-111">Jumper wires</span></span>
- <span data-ttu-id="d4136-112">Raspberry Pi GPIO (選用/建議) </span><span class="sxs-lookup"><span data-stu-id="d4136-112">Raspberry Pi GPIO breakout board (optional/recommended)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [prepare-pi-spi](../includes/prepare-pi-spi.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="d4136-113">準備硬體</span><span class="sxs-lookup"><span data-stu-id="d4136-113">Prepare the hardware</span></span>

<span data-ttu-id="d4136-114">使用硬體元件來建立線路，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="d4136-114">Use the hardware components to build the circuit as depicted in the following diagram:</span></span>

:::image type="content" source="../media/rpi-trimpot_spi-thumb.png" alt-text="Fritzing 圖顯示具有 MCP3008 ADC 和 potentiometer 的電路" lightbox="../media/rpi-trimpot_spi.png":::

<span data-ttu-id="d4136-116">MCP3008 使用串列周邊介面 (SPI) 來進行通訊。</span><span class="sxs-lookup"><span data-stu-id="d4136-116">The MCP3008 uses Serial Peripheral Interface (SPI) to communicate.</span></span> <span data-ttu-id="d4136-117">以下是從 MCP3008 到 Raspberry Pi 和 potentiometer 的連接：</span><span class="sxs-lookup"><span data-stu-id="d4136-117">The following are the connections from the MCP3008 to the Raspberry Pi and potentiometer:</span></span>

- <span data-ttu-id="d4136-118">V<sub>DD</sub> 至 3.3 v (以紅色) 顯示</span><span class="sxs-lookup"><span data-stu-id="d4136-118">V<sub>DD</sub> to 3.3V (shown in red)</span></span>
- <span data-ttu-id="d4136-119">3.3 V (red) 的 v<sub>參考</sub></span><span class="sxs-lookup"><span data-stu-id="d4136-119">V<sub>REF</sub> to 3.3V (red)</span></span>
- <span data-ttu-id="d4136-120">AGND 至地面 (黑色) </span><span class="sxs-lookup"><span data-stu-id="d4136-120">AGND to ground (black)</span></span>
- <span data-ttu-id="d4136-121">CLK 至 SCLK (橙色) </span><span class="sxs-lookup"><span data-stu-id="d4136-121">CLK to SCLK (orange)</span></span>
- <span data-ttu-id="d4136-122">D<sub>MISO</sub> (橙色) </span><span class="sxs-lookup"><span data-stu-id="d4136-122">D<sub>OUT</sub> to MISO (orange)</span></span>
- <span data-ttu-id="d4136-123">MOSI (橙色<sub>的</sub> D) </span><span class="sxs-lookup"><span data-stu-id="d4136-123">D<sub>IN</sub> to MOSI (orange)</span></span>
- <span data-ttu-id="d4136-124">CS/SHDN 至 CE0 (綠色) </span><span class="sxs-lookup"><span data-stu-id="d4136-124">CS/SHDN to CE0 (green)</span></span>
- <span data-ttu-id="d4136-125">DGND 至地面 (黑色) </span><span class="sxs-lookup"><span data-stu-id="d4136-125">DGND to ground (black)</span></span>
- <span data-ttu-id="d4136-126">在 potentiometer 上 CH0 至變數 (中間) 釘選 (黃色) </span><span class="sxs-lookup"><span data-stu-id="d4136-126">CH0 to variable (middle) pin on potentiometer (yellow)</span></span>

<span data-ttu-id="d4136-127">提供 3.3 V 和地面給 potentiometer 上的外部針腳。</span><span class="sxs-lookup"><span data-stu-id="d4136-127">Supply 3.3V and ground to the outer pins on the potentiometer.</span></span> <span data-ttu-id="d4136-128">順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="d4136-128">Order is unimportant.</span></span>

<span data-ttu-id="d4136-129">視需要參閱下列引出線圖：</span><span class="sxs-lookup"><span data-stu-id="d4136-129">Refer to the following pinout diagrams as needed:</span></span>

| <span data-ttu-id="d4136-130">MCP3008</span><span class="sxs-lookup"><span data-stu-id="d4136-130">MCP3008</span></span>  | <span data-ttu-id="d4136-131">Raspberry Pi GPIO</span><span class="sxs-lookup"><span data-stu-id="d4136-131">Raspberry Pi GPIO</span></span> |
|----------|-------------------|
| :::image type="content" source="../media/mcp3008-diagram-thumb.png" alt-text="顯示 MCP3008 針腳的圖表" lightbox="../media/mcp3008-diagram.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="顯示 Raspberry Pi GPIO 標頭背面的圖表。Raspberry Pi Foundation 的圖像。" lightbox="../media/gpio-pinout-diagram.png":::<br /><span data-ttu-id="d4136-134">[Raspberry Pi Foundation 的圖像](https://www.raspberrypi.org/documentation/usage/gpio/)。</span><span class="sxs-lookup"><span data-stu-id="d4136-134">[Image courtesy Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/).</span></span>
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="d4136-135">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="d4136-135">Create the app</span></span>

<span data-ttu-id="d4136-136">請在您慣用的開發環境中完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="d4136-136">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="d4136-137">使用 [.NET CLI](../../core/tools/dotnet-new.md) 或 [Visual Studio](../../core/tutorials/with-visual-studio.md)建立新的 .net 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="d4136-137">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="d4136-138">將它命名為 *AdcTutorial*。</span><span class="sxs-lookup"><span data-stu-id="d4136-138">Name it *AdcTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o AdcTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="d4136-139">使用下列程式碼取代 *Program.cs* 的內容：</span><span class="sxs-lookup"><span data-stu-id="d4136-139">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/AdcTutorial/Program.cs" :::

    <span data-ttu-id="d4136-140">在上述程式碼中：</span><span class="sxs-lookup"><span data-stu-id="d4136-140">In the preceding code:</span></span>

    - <span data-ttu-id="d4136-141">`hardwareSpiSettings` 設定為的新實例 `SpiConnectionSettings` 。</span><span class="sxs-lookup"><span data-stu-id="d4136-141">`hardwareSpiSettings` is set to a new instance of `SpiConnectionSettings`.</span></span> <span data-ttu-id="d4136-142">此函數會將 `busId` 參數設定為0，並將 `chipSelectLine` 參數設定為0。</span><span class="sxs-lookup"><span data-stu-id="d4136-142">The constructor sets the `busId` parameter to 0 and the `chipSelectLine` parameter to 0.</span></span>
    - <span data-ttu-id="d4136-143">[Using](../../csharp/whats-new/csharp-8.md#using-declarations)宣告會藉 `SpiDevice` 由呼叫和傳入來建立的實例 `SpiDevice.Create` `hardwareSpiSettings` 。</span><span class="sxs-lookup"><span data-stu-id="d4136-143">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `SpiDevice` by calling `SpiDevice.Create` and passing in `hardwareSpiSettings`.</span></span> <span data-ttu-id="d4136-144">這 `SpiDevice` 代表 SPI 匯流排。</span><span class="sxs-lookup"><span data-stu-id="d4136-144">This `SpiDevice` represents the SPI bus.</span></span> <span data-ttu-id="d4136-145">宣告 `using` 可確保物件已處置，且硬體資源已正確釋放。</span><span class="sxs-lookup"><span data-stu-id="d4136-145">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>
    - <span data-ttu-id="d4136-146">另一個宣告會 `using` 建立的實例 `Mcp3008` ，並將傳遞至函式 `SpiDevice` 。</span><span class="sxs-lookup"><span data-stu-id="d4136-146">Another `using` declaration creates an instance of `Mcp3008` and passes the `SpiDevice` into the constructor.</span></span>
    - <span data-ttu-id="d4136-147">`while`迴圈會無限期地執行。</span><span class="sxs-lookup"><span data-stu-id="d4136-147">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="d4136-148">每個反復專案：</span><span class="sxs-lookup"><span data-stu-id="d4136-148">Each iteration:</span></span>
        1. <span data-ttu-id="d4136-149">藉由呼叫，讀取 ADC 上的 CH0 值 `mcp.Read(0)` 。</span><span class="sxs-lookup"><span data-stu-id="d4136-149">Reads the value of CH0 on the ADC by calling `mcp.Read(0)`.</span></span>
        1. <span data-ttu-id="d4136-150">將值除以10.24。</span><span class="sxs-lookup"><span data-stu-id="d4136-150">Divides the value by 10.24.</span></span> <span data-ttu-id="d4136-151">MCP3008 是10位的 ADC，這表示它會傳回1024個可能的值，範圍是0-1023。</span><span class="sxs-lookup"><span data-stu-id="d4136-151">The MCP3008 is a 10-bit ADC, which means it returns 1024 possible values ranging 0-1023.</span></span> <span data-ttu-id="d4136-152">將值除以10.24 表示以百分比表示值。</span><span class="sxs-lookup"><span data-stu-id="d4136-152">Dividing the value by 10.24 represents the value as a percentage.</span></span>
        1. <span data-ttu-id="d4136-153">將值四捨五入為最接近的整數。</span><span class="sxs-lookup"><span data-stu-id="d4136-153">Rounds the value to the nearest integer.</span></span>
        1. <span data-ttu-id="d4136-154">將值寫入主控台的格式（以百分比表示）。</span><span class="sxs-lookup"><span data-stu-id="d4136-154">Writes the value to the console formatted as a percentage.</span></span>
        1. <span data-ttu-id="d4136-155">睡眠 500 ms。</span><span class="sxs-lookup"><span data-stu-id="d4136-155">Sleeps 500 ms.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="d4136-156">切換至部署目錄並執行可執行檔，以在 Raspberry Pi 上執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d4136-156">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./AdcTutorial
    ```

    <span data-ttu-id="d4136-157">當您旋轉 potentiometer 撥號時，請觀察輸出。</span><span class="sxs-lookup"><span data-stu-id="d4136-157">Observe the output as you rotate the potentiometer dial.</span></span> <span data-ttu-id="d4136-158">這是因為 potentiometer 會將在 ADC 上提供給 CH0 的電壓改變。</span><span class="sxs-lookup"><span data-stu-id="d4136-158">This is due to the potentiometer varying the voltage supplied to CH0 on the ADC.</span></span> <span data-ttu-id="d4136-159">ADC 會比較 CH0 上的輸入電壓與提供給 V<sub>REF</sub> 的參考電壓來產生值。</span><span class="sxs-lookup"><span data-stu-id="d4136-159">The ADC compares the input voltage on CH0 to the reference voltage supplied to V<sub>REF</sub> to generate a value.</span></span>

1. <span data-ttu-id="d4136-160">按 <kbd>Ctrl + C</kbd>來終止程式。</span><span class="sxs-lookup"><span data-stu-id="d4136-160">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="d4136-161">恭喜！</span><span class="sxs-lookup"><span data-stu-id="d4136-161">Congratulations!</span></span> <span data-ttu-id="d4136-162">您已使用 SPI 從類比轉數位轉換器中讀取值。</span><span class="sxs-lookup"><span data-stu-id="d4136-162">You've used SPI to read values from an analog-to-digital converter.</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="d4136-163">取得原始程式碼</span><span class="sxs-lookup"><span data-stu-id="d4136-163">Get the source code</span></span>

<span data-ttu-id="d4136-164">本教學課程的來源 [可在 GitHub 上](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/AdcTutorial)取得。</span><span class="sxs-lookup"><span data-stu-id="d4136-164">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/AdcTutorial).</span></span> <span class="docon docon-navigate-external x-hidden-focus"></span>

## <a name="next-steps"></a><span data-ttu-id="d4136-165">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d4136-165">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d4136-166">瞭解如何使用一般用途的輸入/輸出來閃爍 LED</span><span class="sxs-lookup"><span data-stu-id="d4136-166">Learn to use General Purpose Input/Output to blink an LED</span></span>](../tutorials/blink-led.md)
