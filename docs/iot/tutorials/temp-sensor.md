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
# <a name="read-environmental-conditions-from-a-sensor"></a><span data-ttu-id="e87ff-103">從感應器讀取環境情況</span><span class="sxs-lookup"><span data-stu-id="e87ff-103">Read environmental conditions from a sensor</span></span>

<span data-ttu-id="e87ff-104">IoT 裝置最常見的其中一個案例是偵測環境狀況。</span><span class="sxs-lookup"><span data-stu-id="e87ff-104">One of the most common scenarios for IoT devices is detection of environmental conditions.</span></span> <span data-ttu-id="e87ff-105">有各種感應器可用來監視溫度、濕度、氣壓壓力等等。</span><span class="sxs-lookup"><span data-stu-id="e87ff-105">A variety of sensors are available to monitor temperature, humidity, barometric pressure, and more.</span></span>

<span data-ttu-id="e87ff-106">在本主題中，您將使用 .NET 從感應器讀取環境條件。</span><span class="sxs-lookup"><span data-stu-id="e87ff-106">In this topic, you will use .NET to read environmental conditions from a sensor.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e87ff-107">先決條件</span><span class="sxs-lookup"><span data-stu-id="e87ff-107">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="e87ff-108">[BME280](https://learn.adafruit.com/adafruit-bme280-humidity-barometric-pressure-temperature-sensor-breakout) <span class="docon docon-navigate-external x-hidden-focus"></span> 濕度/氣壓壓力/溫度感應器分類</span><span class="sxs-lookup"><span data-stu-id="e87ff-108">[BME280](https://learn.adafruit.com/adafruit-bme280-humidity-barometric-pressure-temperature-sensor-breakout) <span class="docon docon-navigate-external x-hidden-focus"></span> humidity/barometric pressure/temperature sensor breakout</span></span>
- <span data-ttu-id="e87ff-109">跳線</span><span class="sxs-lookup"><span data-stu-id="e87ff-109">Jumper wires</span></span>
- <span data-ttu-id="e87ff-110">麵包板 (選用) </span><span class="sxs-lookup"><span data-stu-id="e87ff-110">Breadboard (optional)</span></span>
- <span data-ttu-id="e87ff-111">Raspberry Pi GPIO (選用) </span><span class="sxs-lookup"><span data-stu-id="e87ff-111">Raspberry Pi GPIO breakout board (optional)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

> [!IMPORTANT]
> <span data-ttu-id="e87ff-112">有許多 BME280 突破的製造商。</span><span class="sxs-lookup"><span data-stu-id="e87ff-112">There are many manufacturers of BME280 breakouts.</span></span> <span data-ttu-id="e87ff-113">大部分的設計都很類似，而且製造商不應該與功能產生任何差異。</span><span class="sxs-lookup"><span data-stu-id="e87ff-113">Most designs are similar, and the manufacturer shouldn't make any difference to the functionality.</span></span> <span data-ttu-id="e87ff-114">本教學課程會嘗試考慮變化。</span><span class="sxs-lookup"><span data-stu-id="e87ff-114">This tutorial attempts to account for variations.</span></span> <span data-ttu-id="e87ff-115">確定您的 BME280 分類包含 (I2C) 介面的 Inter-Integrated 電路。</span><span class="sxs-lookup"><span data-stu-id="e87ff-115">Ensure your BME280 breakout includes an Inter-Integrated Circuit (I2C) interface.</span></span>

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="e87ff-116">準備硬體</span><span class="sxs-lookup"><span data-stu-id="e87ff-116">Prepare the hardware</span></span>

<span data-ttu-id="e87ff-117">使用硬體元件來建立線路，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="e87ff-117">Use the hardware components to build the circuit as depicted in the following diagram:</span></span>

:::image type="content" source="../media/rpi-bmp280_i2c-thumb.png" alt-text="Fritzing 圖，顯示從 Raspberry Pi 到 BME280 排列面板的連接" lightbox="../media/rpi-bmp280_i2c.png":::

<span data-ttu-id="e87ff-119">以下是從 Raspberry Pi 到 BME280 分組的連接：</span><span class="sxs-lookup"><span data-stu-id="e87ff-119">The following are the connections from the Raspberry Pi to the BME280 breakout:</span></span>

- <span data-ttu-id="e87ff-120">3.3 v 至 VIN *或* 3V3 (以紅色) 顯示</span><span class="sxs-lookup"><span data-stu-id="e87ff-120">3.3V to VIN *OR* 3V3 (shown in red)</span></span>
- <span data-ttu-id="e87ff-121">GND (黑) 的地面</span><span class="sxs-lookup"><span data-stu-id="e87ff-121">Ground to GND (black)</span></span>
- <span data-ttu-id="e87ff-122">SDA (GPIO 2) 至 SDI *或* SDA (blue) </span><span class="sxs-lookup"><span data-stu-id="e87ff-122">SDA (GPIO 2) to SDI *OR* SDA (blue)</span></span>
- <span data-ttu-id="e87ff-123">SCL (GPIO 3) 至 SCK *或* scl (橙色) </span><span class="sxs-lookup"><span data-stu-id="e87ff-123">SCL (GPIO 3) to SCK *OR* SCL (orange)</span></span>

[!INCLUDE [tutorial-rpi-gpio](../includes/tutorial-rpi-gpio.md)]

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="e87ff-124">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="e87ff-124">Create the app</span></span>

<span data-ttu-id="e87ff-125">請在您慣用的開發環境中完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="e87ff-125">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="e87ff-126">使用 [.NET CLI](../../core/tools/dotnet-new.md) 或 [Visual Studio](../../core/tutorials/with-visual-studio.md)建立新的 .net 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="e87ff-126">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="e87ff-127">將它命名為 *SensorTutorial*。</span><span class="sxs-lookup"><span data-stu-id="e87ff-127">Name it *SensorTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o SensorTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="e87ff-128">使用下列程式碼取代 *Program.cs* 的內容：</span><span class="sxs-lookup"><span data-stu-id="e87ff-128">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/SensorTutorial/Program.cs" :::

    <span data-ttu-id="e87ff-129">在上述程式碼中：</span><span class="sxs-lookup"><span data-stu-id="e87ff-129">In the preceding code:</span></span>

    - <span data-ttu-id="e87ff-130">`i2cSettings` 設定為的新實例 `I2cConnectionSettings` 。</span><span class="sxs-lookup"><span data-stu-id="e87ff-130">`i2cSettings` is set to a new instance of `I2cConnectionSettings`.</span></span> <span data-ttu-id="e87ff-131">此函式會將 `busId` 參數設定為1，並將 `deviceAddress` 參數設定為 `Bme280.DefaultI2cAddress` 。</span><span class="sxs-lookup"><span data-stu-id="e87ff-131">The constructor sets the `busId` parameter to 1 and the `deviceAddress` parameter to `Bme280.DefaultI2cAddress`.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="e87ff-132">有些 BME280 的專題製造商會使用次要位址值。</span><span class="sxs-lookup"><span data-stu-id="e87ff-132">Some BME280 breakout manufacturers use the secondary address value.</span></span> <span data-ttu-id="e87ff-133">針對這些裝置，請使用 `Bme280.SecondaryI2cAddress` 。</span><span class="sxs-lookup"><span data-stu-id="e87ff-133">For those devices, use `Bme280.SecondaryI2cAddress`.</span></span>

    - <span data-ttu-id="e87ff-134">[Using](../../csharp/whats-new/csharp-8.md#using-declarations)宣告會藉 `I2cDevice` 由呼叫和傳入來建立的實例 `I2cDevice.Create` `i2cSettings` 。</span><span class="sxs-lookup"><span data-stu-id="e87ff-134">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `I2cDevice` by calling `I2cDevice.Create` and passing in `i2cSettings`.</span></span> <span data-ttu-id="e87ff-135">這 `I2cDevice` 代表 I2C 匯流排。</span><span class="sxs-lookup"><span data-stu-id="e87ff-135">This `I2cDevice` represents the I2C bus.</span></span> <span data-ttu-id="e87ff-136">宣告 `using` 可確保物件已處置，且硬體資源已正確釋放。</span><span class="sxs-lookup"><span data-stu-id="e87ff-136">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>
    - <span data-ttu-id="e87ff-137">另一個宣告會 `using` 建立的實例 `Bme280` ，以代表感應器。</span><span class="sxs-lookup"><span data-stu-id="e87ff-137">Another `using` declaration creates an instance of `Bme280` to represent the sensor.</span></span> <span data-ttu-id="e87ff-138">`I2cDevice`會在函式中傳遞。</span><span class="sxs-lookup"><span data-stu-id="e87ff-138">The `I2cDevice` is passed in the constructor.</span></span>
    - <span data-ttu-id="e87ff-139">藉由呼叫，可取得晶片使用晶片目前 (預設) 設定來測量的所需時間 `GetMeasurementDuration` 。</span><span class="sxs-lookup"><span data-stu-id="e87ff-139">The time required for the chip to take measurements with the chip's current (default) settings is retrieved by calling `GetMeasurementDuration`.</span></span>
    - <span data-ttu-id="e87ff-140">`while`迴圈會無限期地執行。</span><span class="sxs-lookup"><span data-stu-id="e87ff-140">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="e87ff-141">每個反復專案：</span><span class="sxs-lookup"><span data-stu-id="e87ff-141">Each iteration:</span></span>
        1. <span data-ttu-id="e87ff-142">清除主控台。</span><span class="sxs-lookup"><span data-stu-id="e87ff-142">Clears the console.</span></span>
        1. <span data-ttu-id="e87ff-143">將電源模式設定為 `Bmx280PowerMode.Forced` 。</span><span class="sxs-lookup"><span data-stu-id="e87ff-143">Sets the power mode to `Bmx280PowerMode.Forced`.</span></span> <span data-ttu-id="e87ff-144">這會強制晶片執行一項測量、儲存結果，然後進入睡眠狀態。</span><span class="sxs-lookup"><span data-stu-id="e87ff-144">This forces the chip to perform one measurement, store the results, and then sleep.</span></span>
        1. <span data-ttu-id="e87ff-145">讀取溫度、壓力、濕度和高度的值。</span><span class="sxs-lookup"><span data-stu-id="e87ff-145">Reads the values for temperature, pressure, humidity, and altitude.</span></span>

            > [!NOTE]
            > <span data-ttu-id="e87ff-146">高度是由裝置系結計算。</span><span class="sxs-lookup"><span data-stu-id="e87ff-146">Altitude is calculated by the device binding.</span></span> <span data-ttu-id="e87ff-147">這項使用的多載 `TryReadAltitude` 表示產生估計值的海洋級壓力。</span><span class="sxs-lookup"><span data-stu-id="e87ff-147">This overload of `TryReadAltitude` uses mean sea level pressure to generate an estimate.</span></span>

        1. <span data-ttu-id="e87ff-148">將目前的環境條件寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="e87ff-148">Writes the current environmental conditions to the console.</span></span>
        1. <span data-ttu-id="e87ff-149">睡眠 1000 ms。</span><span class="sxs-lookup"><span data-stu-id="e87ff-149">Sleeps 1000 ms.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="e87ff-150">切換至部署目錄並執行可執行檔，以在 Raspberry Pi 上執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="e87ff-150">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./SensorTutorial
    ```

    <span data-ttu-id="e87ff-151">觀察主控台中的感應器輸出。</span><span class="sxs-lookup"><span data-stu-id="e87ff-151">Observe the sensor output in the console.</span></span>

1. <span data-ttu-id="e87ff-152">按 <kbd>Ctrl + C</kbd>來終止程式。</span><span class="sxs-lookup"><span data-stu-id="e87ff-152">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="e87ff-153">恭喜！</span><span class="sxs-lookup"><span data-stu-id="e87ff-153">Congratulations!</span></span> <span data-ttu-id="e87ff-154">您已使用 I2C 來讀取溫度/濕度/氣壓壓力感應器的值！</span><span class="sxs-lookup"><span data-stu-id="e87ff-154">You've used I2C to read values from a temperature/humidity/barometric pressure sensor!</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="e87ff-155">取得原始程式碼</span><span class="sxs-lookup"><span data-stu-id="e87ff-155">Get the source code</span></span>

<span data-ttu-id="e87ff-156">本教學課程的來源 [可在 GitHub 上](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/SensorTutorial)取得 <span class="docon docon-navigate-external x-hidden-focus"></span> 。</span><span class="sxs-lookup"><span data-stu-id="e87ff-156">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/SensorTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e87ff-157">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e87ff-157">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e87ff-158">瞭解如何在 LCD 上顯示文字</span><span class="sxs-lookup"><span data-stu-id="e87ff-158">Learn how to display text on an LCD</span></span>](../tutorials/lcd-display.md)
