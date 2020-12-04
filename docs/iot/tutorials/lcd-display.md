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
# <a name="display-text-on-an-lcd"></a><span data-ttu-id="dc3d1-103">在 LCD 上顯示文字</span><span class="sxs-lookup"><span data-stu-id="dc3d1-103">Display text on an LCD</span></span>

<span data-ttu-id="dc3d1-104">LCD 字元顯示適用于顯示資訊，而不需要外部監視器。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-104">LCD character displays are useful for displaying information without the need for an external monitor.</span></span> <span data-ttu-id="dc3d1-105">一般的 LCD 字元顯示可以直接連接至 GPIO 針腳，但這種方法需要使用最多10個 GPIO pin。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-105">Common LCD character displays can be connected directly to the GPIO pins, but such an approach requires the use of up to 10 GPIO pins.</span></span> <span data-ttu-id="dc3d1-106">對於需要連接到裝置組合的案例，專很多的 GPIO 標頭到字元顯示通常不切實際。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-106">For scenarios that require connecting to a combination of devices, devoting so much of the GPIO header to a character display is often impractical.</span></span>

<span data-ttu-id="dc3d1-107">許多製造商會使用整合 GPIO 擴充器來銷售 20x4 LCD 字元顯示器。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-107">Many manufacturers sell 20x4 LCD character displays with an integrated GPIO expander.</span></span> <span data-ttu-id="dc3d1-108">字元顯示會直接連接到 GPIO 展開器，然後透過 Inter-Integrated 電路 (I2C) 序列通訊協定連接到 Raspberry Pi。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-108">The character display connects directly to the GPIO expander, which then connects to the Raspberry Pi via the Inter-Integrated Circuit (I2C) serial protocol.</span></span>

<span data-ttu-id="dc3d1-109">在本主題中，您將使用 [.NET]，以使用 I2C GPIO 擴充程式來顯示 LCD 字元顯示器上的文字。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-109">In this topic, you will use .NET to display text on an LCD character display using an I2C GPIO expander.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dc3d1-110">先決條件</span><span class="sxs-lookup"><span data-stu-id="dc3d1-110">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="dc3d1-111">[使用 I2C 介面 20X4 LCD 字元顯示](https://www.bing.com/images/search?q=20x4+lcd+display+with+i2c)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="dc3d1-111">[20x4 LCD Character Display with I2C interface](https://www.bing.com/images/search?q=20x4+lcd+display+with+i2c) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
- <span data-ttu-id="dc3d1-112">跳線</span><span class="sxs-lookup"><span data-stu-id="dc3d1-112">Jumper wires</span></span>
- <span data-ttu-id="dc3d1-113">麵包板 (選用/建議) </span><span class="sxs-lookup"><span data-stu-id="dc3d1-113">Breadboard (optional/recommended)</span></span>
- <span data-ttu-id="dc3d1-114">Raspberry Pi GPIO (選用/建議) </span><span class="sxs-lookup"><span data-stu-id="dc3d1-114">Raspberry Pi GPIO breakout board (optional/recommended)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

> [!NOTE]
> <span data-ttu-id="dc3d1-115">有許多製造商的 LCD 字元顯示器。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-115">There are many manufacturers of LCD character displays.</span></span> <span data-ttu-id="dc3d1-116">大部分的設計都是一樣的，製造商也不應該與功能產生任何差異。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-116">Most designs are identical, and the manufacturer shouldn't make any difference to the functionality.</span></span> <span data-ttu-id="dc3d1-117">本教學課程是以「 [SUNFOUNDER LCD2004](https://www.sunfounder.com/lcd2004-module.html) 」進行參考 <span class="docon docon-navigate-external x-hidden-focus"></span> 。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-117">For reference, this tutorial was developed with the [SunFounder LCD2004](https://www.sunfounder.com/lcd2004-module.html) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="dc3d1-118">準備硬體</span><span class="sxs-lookup"><span data-stu-id="dc3d1-118">Prepare the hardware</span></span>

<span data-ttu-id="dc3d1-119">使用跳線來將 I2C GPIO 擴充器上的四個圖釘連接至 Raspberry Pi，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dc3d1-119">Use jumper wires to connect the four pins on the I2C GPIO expander to the Raspberry Pi as follows:</span></span>

- <span data-ttu-id="dc3d1-120">GND 至地面</span><span class="sxs-lookup"><span data-stu-id="dc3d1-120">GND to ground</span></span>
- <span data-ttu-id="dc3d1-121">與5V 的 VCC</span><span class="sxs-lookup"><span data-stu-id="dc3d1-121">VCC to 5V</span></span>
- <span data-ttu-id="dc3d1-122">SDA 至 SDA (GPIO 2) </span><span class="sxs-lookup"><span data-stu-id="dc3d1-122">SDA to SDA (GPIO 2)</span></span>
- <span data-ttu-id="dc3d1-123">SCL 至 SCL (GPIO 3) </span><span class="sxs-lookup"><span data-stu-id="dc3d1-123">SCL to SCL (GPIO 3)</span></span>

<span data-ttu-id="dc3d1-124">如有需要，請參閱下列資料：</span><span class="sxs-lookup"><span data-stu-id="dc3d1-124">Refer to the following figures as needed:</span></span>

| <span data-ttu-id="dc3d1-125">I2C 介面 (顯示) 的背面</span><span class="sxs-lookup"><span data-stu-id="dc3d1-125">I2C interface (back of display)</span></span> | <span data-ttu-id="dc3d1-126">Raspberry Pi GPIO</span><span class="sxs-lookup"><span data-stu-id="dc3d1-126">Raspberry Pi GPIO</span></span> |
|---------------------------------|-------------------|
| :::image type="content" source="../media/character-display-i2c-thumb.png" alt-text="顯示 I2C GPIO 展開器之字元顯示背面的影像。" lightbox="../media/character-display-i2c.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="顯示 Raspberry Pi GPIO 標頭背面的圖表。Raspberry Pi Foundation 的圖像。" lightbox="../media/gpio-pinout-diagram.png":::<br /><span data-ttu-id="dc3d1-129">[Raspberry Pi Foundation 的圖像](https://www.raspberrypi.org/documentation/usage/gpio/) <span class="docon docon-navigate-external x-hidden-focus"></span> 。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-129">[Image courtesy Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="dc3d1-130">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="dc3d1-130">Create the app</span></span>

<span data-ttu-id="dc3d1-131">請在您慣用的開發環境中完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="dc3d1-131">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="dc3d1-132">使用 [.NET CLI](../../core/tools/dotnet-new.md) 或 [Visual Studio](../../core/tutorials/with-visual-studio.md)建立新的 .net 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-132">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="dc3d1-133">將它命名為 *LcdTutorial*。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-133">Name it *LcdTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o LcdTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="dc3d1-134">使用下列程式碼取代 *Program.cs* 的內容：</span><span class="sxs-lookup"><span data-stu-id="dc3d1-134">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/LcdTutorial/Program.cs" :::

    <span data-ttu-id="dc3d1-135">在上述程式碼中：</span><span class="sxs-lookup"><span data-stu-id="dc3d1-135">In the preceding code:</span></span>

    - <span data-ttu-id="dc3d1-136">[Using](../../csharp/whats-new/csharp-8.md#using-declarations)宣告會藉 `I2cDevice` 由呼叫 `I2cDevice.Create` 並傳入 `I2cConnectionSettings` 具有 `busId` 和參數的新，來建立的實例 `deviceAddress` 。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-136">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `I2cDevice` by calling `I2cDevice.Create` and passing in a new `I2cConnectionSettings` with the `busId` and `deviceAddress` parameters.</span></span> <span data-ttu-id="dc3d1-137">這 `I2cDevice` 代表 I2C 匯流排。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-137">This `I2cDevice` represents the I2C bus.</span></span> <span data-ttu-id="dc3d1-138">宣告 `using` 可確保物件已處置，且硬體資源已正確釋放。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-138">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>

        > [!WARNING]
        > <span data-ttu-id="dc3d1-139">GPIO 擴充器的裝置位址取決於製造商使用的晶片。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-139">The device address for the GPIO expander depends on the chip used by the manufacturer.</span></span> <span data-ttu-id="dc3d1-140">具有 PCF8574 的 GPIO 展開器會使用該位址 `0x27` ，而使用 PCF8574A 晶片的則使用該位址 `0x3F` 。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-140">GPIO expanders equipped with a PCF8574 use the address `0x27`, while those using PCF8574A chips use `0x3F`.</span></span> <span data-ttu-id="dc3d1-141">請參閱您的 LCD 檔。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-141">Consult your LCD's documentation.</span></span>

    - <span data-ttu-id="dc3d1-142">另一個宣告會 `using` 建立的實例 `Pcf8574` ，並將傳遞至函式 `I2cDevice` 。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-142">Another `using` declaration creates an instance of `Pcf8574` and passes the `I2cDevice` into the constructor.</span></span> <span data-ttu-id="dc3d1-143">此實例代表 GPIO 展開器。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-143">This instance represents the GPIO expander.</span></span>
    - <span data-ttu-id="dc3d1-144">另一個宣告會 `using` 建立的實例 `Lcd2004` ，以代表顯示。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-144">Another `using` declaration creates an instance of `Lcd2004` to represent the display.</span></span> <span data-ttu-id="dc3d1-145">會將數個參數傳遞給描述要用來與 GPIO 展開器通訊的設定的函式。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-145">Several parameters are passed to the constructor describing the settings to use to communicate with the GPIO expander.</span></span> <span data-ttu-id="dc3d1-146">GPIO 擴充項會以參數形式傳遞 `controller` 。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-146">The GPIO expander is passed as the `controller` parameter.</span></span>
    - <span data-ttu-id="dc3d1-147">`while`迴圈會無限期地執行。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-147">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="dc3d1-148">每個反復專案：</span><span class="sxs-lookup"><span data-stu-id="dc3d1-148">Each iteration:</span></span>
        1. <span data-ttu-id="dc3d1-149">清除顯示。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-149">Clears the display.</span></span>
        1. <span data-ttu-id="dc3d1-150">將游標位置設定為目前行上的第一個位置。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-150">Sets the cursor position to the first position on the current line.</span></span>
        1. <span data-ttu-id="dc3d1-151">將目前的時間寫入目前游標位置的顯示位置。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-151">Writes the current time to the display at the current cursor position.</span></span>
        1. <span data-ttu-id="dc3d1-152">反覆運算目前的行計數器。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-152">Iterates the current line counter.</span></span>
        1. <span data-ttu-id="dc3d1-153">睡眠 1000 ms。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-153">Sleeps 1000 ms.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="dc3d1-154">切換至部署目錄並執行可執行檔，以在 Raspberry Pi 上執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-154">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./LcdTutorial
    ```

    <span data-ttu-id="dc3d1-155">觀察每一行顯示的 LCD 字元顯示是否為目前的時間。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-155">Observe the LCD character display as the current time displays on each line.</span></span>

    > [!TIP]
    > <span data-ttu-id="dc3d1-156">如果顯示器燈亮，但您沒有看到任何文字，請嘗試調整顯示器背面的對比撥號。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-156">If the display is lit but you don't see any text, try adjusting the contrast dial on the back of the display.</span></span>

1. <span data-ttu-id="dc3d1-157">按 <kbd>Ctrl + C</kbd>來終止程式。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-157">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="dc3d1-158">恭喜！</span><span class="sxs-lookup"><span data-stu-id="dc3d1-158">Congratulations!</span></span> <span data-ttu-id="dc3d1-159">您已在 LCD 上使用 I2C 和 GPIO 擴充程式顯示文字！</span><span class="sxs-lookup"><span data-stu-id="dc3d1-159">You've displayed text on an LCD using a I2C and a GPIO expander!</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="dc3d1-160">取得原始程式碼</span><span class="sxs-lookup"><span data-stu-id="dc3d1-160">Get the source code</span></span>

<span data-ttu-id="dc3d1-161">本教學課程的來源 [可在 GitHub 上](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/LcdTutorial)取得 <span class="docon docon-navigate-external x-hidden-focus"></span> 。</span><span class="sxs-lookup"><span data-stu-id="dc3d1-161">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/LcdTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="dc3d1-162">後續步驟</span><span class="sxs-lookup"><span data-stu-id="dc3d1-162">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dc3d1-163">瞭解如何使用一般用途的輸入/輸出來閃爍 LED</span><span class="sxs-lookup"><span data-stu-id="dc3d1-163">Learn to use General Purpose Input/Output to blink an LED</span></span>](../tutorials/blink-led.md)
