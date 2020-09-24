---
title: Windows Form 組態區段
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
ms.openlocfilehash: 2d518ec03602580f3c5d00ef2901ff7d7ac1d81b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148499"
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="15281-102">Windows Form 組態區段</span><span class="sxs-lookup"><span data-stu-id="15281-102">Windows Forms Configuration Section</span></span>

<span data-ttu-id="15281-103">Windows Forms 組態設定允許 Windows Forms 應用程式儲存並擷取有關自訂應用程式設定 (例如多重監視器支援、高 DPI 支援，以及其他預先定義的組態設定) 的資訊。</span><span class="sxs-lookup"><span data-stu-id="15281-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="15281-104">Windows Forms 應用程式組態設定是儲存在應用程式組態檔的 `System.Windows.Forms.ApplicationConfigurationSection` 元素中。</span><span class="sxs-lookup"><span data-stu-id="15281-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="15281-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="15281-105">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="15281-106">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="15281-106">Attributes and elements</span></span>

<span data-ttu-id="15281-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="15281-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="15281-108">屬性</span><span class="sxs-lookup"><span data-stu-id="15281-108">Attributes</span></span>

<span data-ttu-id="15281-109">無。</span><span class="sxs-lookup"><span data-stu-id="15281-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="15281-110">子元素</span><span class="sxs-lookup"><span data-stu-id="15281-110">Child elements</span></span>

<span data-ttu-id="15281-111">項目</span><span class="sxs-lookup"><span data-stu-id="15281-111">Element</span></span>  |<span data-ttu-id="15281-112">描述</span><span class="sxs-lookup"><span data-stu-id="15281-112">Description</span></span> |
---------|---------|
[`<add>`](windows-forms-add-configuration-element.md) | <span data-ttu-id="15281-113">新增具有指定值的組態設定金鑰</span><span class="sxs-lookup"><span data-stu-id="15281-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="15281-114">父元素</span><span class="sxs-lookup"><span data-stu-id="15281-114">Parent elements</span></span>

<span data-ttu-id="15281-115">項目</span><span class="sxs-lookup"><span data-stu-id="15281-115">Element</span></span>  |<span data-ttu-id="15281-116">描述</span><span class="sxs-lookup"><span data-stu-id="15281-116">Description</span></span> |
---------|---------|
[\<configuration>](../configuration-element.md) | <span data-ttu-id="15281-117">通用語言執行平台和 Windows Forms 應用程式所使用之每個組態檔中的根元素</span><span class="sxs-lookup"><span data-stu-id="15281-117">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="15281-118">備註</span><span class="sxs-lookup"><span data-stu-id="15281-118">Remarks</span></span>

<span data-ttu-id="15281-119">從 .NET Framework 4.7 開始，`<System.Windows.Forms.ApplicationConfigurationSection>` 元素能允許您設定 Windows Forms 應用程式，以利用 .NET Framework 最新版本中的新增功能。</span><span class="sxs-lookup"><span data-stu-id="15281-119">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span>

<span data-ttu-id="15281-120">`<System.Windows.Forms.ApplicationConfigurationSection>`元素可以包含一或多個子專案 [`<add>`](windows-forms-add-configuration-element.md) ，每個專案都定義特定的設定。</span><span class="sxs-lookup"><span data-stu-id="15281-120">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="15281-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15281-121">See also</span></span>

- [<span data-ttu-id="15281-122">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="15281-122">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="15281-123">Windows Forms 中的高 DPI 支援</span><span class="sxs-lookup"><span data-stu-id="15281-123">High DPI Support in Windows Forms</span></span>](/dotnet/desktop/winforms/high-dpi-support-in-windows-forms)
