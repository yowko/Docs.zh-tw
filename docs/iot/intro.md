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
# <a name="develop-apps-for-iot-devices-with-the-net-iot-libraries"></a>使用 .NET IoT 程式庫開發 IoT 裝置的應用程式

.NET 可在各種不同的平臺和架構上執行。 支援 (IoT) 板（例如 Raspberry Pi 和 Hummingboard）的常見物聯網。 IoT 應用程式通常會與特定硬體互動，例如感應器、類比到數位轉換器和 LCD 裝置。 .NET IoT 程式庫可實現這些案例。

## <a name="video-overview"></a>影片概觀

<!--markdownlint-disable MD034 -->
> [!VIDEO https://channel9.msdn.com/Series/IoT-101/Intro-to-IOT-with-NET-Core-1-of-9/player]

## <a name="libraries"></a>程式庫

.NET IoT 程式庫包含兩個 NuGet 套件：

- [System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio/) <span class="docon docon-navigate-external x-hidden-focus"></span>
- [Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings/) <span class="docon docon-navigate-external x-hidden-focus"></span>

### <a name="systemdevicegpio"></a>System.Device.Gpio

`System.Device.Gpio` 支援各種不同的通訊協定，以便與低層級的硬體 pin 互動以控制裝置。 其中包含：

- 一般用途的 i/o (GPIO) 
-  (I2C) 的 Inter-Integrated 電路
- 串列週邊介面 (SPI) 
- 脈衝寬度調製 (PWM) 
- 序列埠

### <a name="iotdevicebindings"></a>Iot.Device.Bindings

`Iot.Device.Bindings`封裝：

* 包含 [裝置](https://github.com/dotnet/iot/blob/master/src/devices/README.md)系結 <span class="docon docon-navigate-external x-hidden-focus"></span> ，以藉由包裝 system.servicemodel 來簡化應用程式開發。
* 是支援社區，而且會持續新增其他系結。

常用的裝置系結包括：

- [CharacterLcd-LCD 字元顯示](https://github.com/dotnet/iot/tree/master/src/devices/CharacterLcd)<span class="docon docon-navigate-external x-hidden-focus"></span>
- [SN74HC595-8 位 shift register](https://github.com/dotnet/iot/tree/master/src/devices/Sn74hc595)<span class="docon docon-navigate-external x-hidden-focus"></span>
- [BrickPi3](https://github.com/dotnet/iot/tree/master/src/devices/BrickPi3)<span class="docon docon-navigate-external x-hidden-focus"></span>
- [Max7219 導向的矩陣驅動程式](https://github.com/dotnet/iot/tree/master/src/devices/Max7219)<span class="docon docon-navigate-external x-hidden-focus"></span>
- [RGBLedMatrix-RGB LED 矩陣](https://github.com/dotnet/iot/tree/master/src/devices/RGBLedMatrix)<span class="docon docon-navigate-external x-hidden-focus"></span>

## <a name="supported-operating-systems"></a>支援的作業系統

`System.Device.Gpio` 支援 ARM/ARM64 和 Windows 10 IoT 核心版的大部分 Linux 版本都可支援。

> [!TIP]
> 針對 Raspberry Pi，建議使用先前 Raspbian) 的[Raspberry PI 作業系統](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) <span class="docon docon-navigate-external x-hidden-focus"></span> (。  

## <a name="supported-hardware-platforms"></a>支援的硬體平臺

`System.Device.Gpio` 與大部分的單一面板平臺相容。 建議的平臺是 Raspberry Pi (2 和更新版本) 和 Hummingboard。 其他已知相容的平臺是 BeagleBoard 和 ODROID。

使用 USB 至 SPI/I2C 橋接器可支援電腦平臺。

> [!IMPORTANT]
> ARMv6 架構裝置不支援 .NET，包括 Raspberry Pi 2 之前的 Raspberry Pi 零和 Raspberry Pi 裝置。

## <a name="resources"></a>資源

- [Github 上的 .Net IoT 程式庫](https://github.com/dotnet/iot)<span class="docon docon-navigate-external x-hidden-focus"></span>
