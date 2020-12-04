---
title: 使用 .NET IoT 程式庫開發 IoT 裝置的應用程式
description: 瞭解如何使用 .NET 來建立 IoT 裝置和案例的應用程式。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: overview
ms.prod: dotnet
ms.openlocfilehash: c3d05ec5b05780f91404c3c27e91bcd602b0faeb
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "96586630"
---
# <a name="develop-apps-for-iot-devices-with-the-net-iot-libraries"></a><span data-ttu-id="000b7-103">使用 .NET IoT 程式庫開發 IoT 裝置的應用程式</span><span class="sxs-lookup"><span data-stu-id="000b7-103">Develop apps for IoT devices with the .NET IoT Libraries</span></span>

<span data-ttu-id="000b7-104">.NET 可在各種不同的平臺和架構上執行。</span><span class="sxs-lookup"><span data-stu-id="000b7-104">.NET runs on a variety of platforms and architectures.</span></span> <span data-ttu-id="000b7-105">支援 (IoT) 板（例如 Raspberry Pi 和 Hummingboard）的常見物聯網。</span><span class="sxs-lookup"><span data-stu-id="000b7-105">Common Internet of things (IoT) boards, such as Raspberry Pi and Hummingboard, are supported.</span></span> <span data-ttu-id="000b7-106">IoT 應用程式通常會與特定硬體互動，例如感應器、類比到數位轉換器和 LCD 裝置。</span><span class="sxs-lookup"><span data-stu-id="000b7-106">IoT apps typically interact with specialized hardware, such as sensors, analog-to-digital converters, and LCD devices.</span></span> <span data-ttu-id="000b7-107">.NET IoT 程式庫可實現這些案例。</span><span class="sxs-lookup"><span data-stu-id="000b7-107">The .NET IoT Libraries enable these scenarios.</span></span>

## <a name="video-overview"></a><span data-ttu-id="000b7-108">影片概觀</span><span class="sxs-lookup"><span data-stu-id="000b7-108">Video overview</span></span>

<!--markdownlint-disable MD034 -->
> [!VIDEO https://channel9.msdn.com/Series/IoT-101/Intro-to-IOT-with-NET-Core-1-of-9/player]

## <a name="libraries"></a><span data-ttu-id="000b7-109">程式庫</span><span class="sxs-lookup"><span data-stu-id="000b7-109">Libraries</span></span>

<span data-ttu-id="000b7-110">.NET IoT 程式庫包含兩個 NuGet 套件：</span><span class="sxs-lookup"><span data-stu-id="000b7-110">The .NET IoT Libraries are composed of two NuGet packages:</span></span>

- <span data-ttu-id="000b7-111">[System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio/) <span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="000b7-111">[System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio/) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
- <span data-ttu-id="000b7-112">[Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings/) <span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="000b7-112">[Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings/) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>

### <a name="systemdevicegpio"></a><span data-ttu-id="000b7-113">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="000b7-113">System.Device.Gpio</span></span>

<span data-ttu-id="000b7-114">`System.Device.Gpio` 支援各種不同的通訊協定，以便與低層級的硬體 pin 互動以控制裝置。</span><span class="sxs-lookup"><span data-stu-id="000b7-114">`System.Device.Gpio` supports a variety of protocols for interacting with low-level hardware pins to control devices.</span></span> <span data-ttu-id="000b7-115">其中包含：</span><span class="sxs-lookup"><span data-stu-id="000b7-115">These include:</span></span>

- <span data-ttu-id="000b7-116">一般用途的 i/o (GPIO) </span><span class="sxs-lookup"><span data-stu-id="000b7-116">General-purpose I/O (GPIO)</span></span>
- <span data-ttu-id="000b7-117"> (I2C) 的 Inter-Integrated 電路</span><span class="sxs-lookup"><span data-stu-id="000b7-117">Inter-Integrated Circuit (I2C)</span></span>
- <span data-ttu-id="000b7-118">串列週邊介面 (SPI) </span><span class="sxs-lookup"><span data-stu-id="000b7-118">Serial Peripheral Interface (SPI)</span></span>
- <span data-ttu-id="000b7-119">脈衝寬度調製 (PWM) </span><span class="sxs-lookup"><span data-stu-id="000b7-119">Pulse Width Modulation (PWM)</span></span>
- <span data-ttu-id="000b7-120">序列埠</span><span class="sxs-lookup"><span data-stu-id="000b7-120">Serial port</span></span>

### <a name="iotdevicebindings"></a><span data-ttu-id="000b7-121">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="000b7-121">Iot.Device.Bindings</span></span>

<span data-ttu-id="000b7-122">`Iot.Device.Bindings`封裝：</span><span class="sxs-lookup"><span data-stu-id="000b7-122">The `Iot.Device.Bindings` package:</span></span>

* <span data-ttu-id="000b7-123">包含 [裝置](https://github.com/dotnet/iot/blob/master/src/devices/README.md)系結 <span class="docon docon-navigate-external x-hidden-focus"></span> ，以藉由包裝 system.servicemodel 來簡化應用程式開發。</span><span class="sxs-lookup"><span data-stu-id="000b7-123">Contains [device bindings](https://github.com/dotnet/iot/blob/master/src/devices/README.md) <span class="docon docon-navigate-external x-hidden-focus"></span> to streamline app development by wrapping System.Device.Gpio.</span></span>
* <span data-ttu-id="000b7-124">是支援社區，而且會持續新增其他系結。</span><span class="sxs-lookup"><span data-stu-id="000b7-124">Is community-supported, and additional bindings are added continually.</span></span>

<span data-ttu-id="000b7-125">常用的裝置系結包括：</span><span class="sxs-lookup"><span data-stu-id="000b7-125">Commonly used device bindings include:</span></span>

- <span data-ttu-id="000b7-126">[CharacterLcd-LCD 字元顯示](https://github.com/dotnet/iot/tree/master/src/devices/CharacterLcd)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="000b7-126">[CharacterLcd - LCD character display](https://github.com/dotnet/iot/tree/master/src/devices/CharacterLcd) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
- <span data-ttu-id="000b7-127">[SN74HC595-8 位 shift register](https://github.com/dotnet/iot/tree/master/src/devices/Sn74hc595)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="000b7-127">[SN74HC595 - 8-bit shift register](https://github.com/dotnet/iot/tree/master/src/devices/Sn74hc595) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
- <span data-ttu-id="000b7-128">[BrickPi3](https://github.com/dotnet/iot/tree/master/src/devices/BrickPi3)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="000b7-128">[BrickPi3](https://github.com/dotnet/iot/tree/master/src/devices/BrickPi3) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
- <span data-ttu-id="000b7-129">[Max7219 導向的矩陣驅動程式](https://github.com/dotnet/iot/tree/master/src/devices/Max7219)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="000b7-129">[Max7219 - LED Matrix driver](https://github.com/dotnet/iot/tree/master/src/devices/Max7219) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
- <span data-ttu-id="000b7-130">[RGBLedMatrix-RGB LED 矩陣](https://github.com/dotnet/iot/tree/master/src/devices/RGBLedMatrix)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="000b7-130">[RGBLedMatrix - RGB LED Matrix](https://github.com/dotnet/iot/tree/master/src/devices/RGBLedMatrix) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="000b7-131">支援的作業系統</span><span class="sxs-lookup"><span data-stu-id="000b7-131">Supported operating systems</span></span>

<span data-ttu-id="000b7-132">`System.Device.Gpio` 支援 ARM/ARM64 和 Windows 10 IoT 核心版的大部分 Linux 版本都可支援。</span><span class="sxs-lookup"><span data-stu-id="000b7-132">`System.Device.Gpio` is supported on most versions of Linux that support ARM/ARM64 and Windows 10 IoT Core.</span></span>

> [!TIP]
> <span data-ttu-id="000b7-133">針對 Raspberry Pi，建議使用先前 Raspbian) 的[Raspberry PI 作業系統](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) <span class="docon docon-navigate-external x-hidden-focus"></span> (。  </span><span class="sxs-lookup"><span data-stu-id="000b7-133">For Raspberry Pi, [Raspberry Pi OS](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)  <span class="docon docon-navigate-external x-hidden-focus"></span> (formerly Raspbian) is recommended.</span></span>

## <a name="supported-hardware-platforms"></a><span data-ttu-id="000b7-134">支援的硬體平臺</span><span class="sxs-lookup"><span data-stu-id="000b7-134">Supported hardware platforms</span></span>

<span data-ttu-id="000b7-135">`System.Device.Gpio` 與大部分的單一面板平臺相容。</span><span class="sxs-lookup"><span data-stu-id="000b7-135">`System.Device.Gpio` is compatible with most single-board platforms.</span></span> <span data-ttu-id="000b7-136">建議的平臺是 Raspberry Pi (2 和更新版本) 和 Hummingboard。</span><span class="sxs-lookup"><span data-stu-id="000b7-136">Recommended platforms are Raspberry Pi (2 and greater) and Hummingboard.</span></span> <span data-ttu-id="000b7-137">其他已知相容的平臺是 BeagleBoard 和 ODROID。</span><span class="sxs-lookup"><span data-stu-id="000b7-137">Other platforms known to be compatible are BeagleBoard and ODROID.</span></span>

<span data-ttu-id="000b7-138">使用 USB 至 SPI/I2C 橋接器可支援電腦平臺。</span><span class="sxs-lookup"><span data-stu-id="000b7-138">PC platforms are supported via the use of a USB to SPI/I2C bridge.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="000b7-139">ARMv6 架構裝置不支援 .NET，包括 Raspberry Pi 2 之前的 Raspberry Pi 零和 Raspberry Pi 裝置。</span><span class="sxs-lookup"><span data-stu-id="000b7-139">.NET is not supported on ARMv6 architecture devices, including Raspberry Pi Zero and Raspberry Pi devices prior to Raspberry Pi 2.</span></span>

## <a name="resources"></a><span data-ttu-id="000b7-140">資源</span><span class="sxs-lookup"><span data-stu-id="000b7-140">Resources</span></span>

- <span data-ttu-id="000b7-141">[Github 上的 .Net IoT 程式庫](https://github.com/dotnet/iot)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="000b7-141">[.NET IoT Libraries on Github](https://github.com/dotnet/iot) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
