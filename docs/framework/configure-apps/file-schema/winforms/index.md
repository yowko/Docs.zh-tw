---
title: Windows Form 組態區段
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e76e11ef8bb39d72cb16655c948354bc326e75bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913091"
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="ec585-102">Windows Form 組態區段</span><span class="sxs-lookup"><span data-stu-id="ec585-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="ec585-103">Windows Forms 組態設定允許 Windows Forms 應用程式儲存並擷取有關自訂應用程式設定 (例如多重監視器支援、高 DPI 支援，以及其他預先定義的組態設定) 的資訊。</span><span class="sxs-lookup"><span data-stu-id="ec585-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="ec585-104">Windows Forms 應用程式組態設定是儲存在應用程式組態檔的 `System.Windows.Forms.ApplicationConfigurationSection` 元素中。</span><span class="sxs-lookup"><span data-stu-id="ec585-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="ec585-105">語法</span><span class="sxs-lookup"><span data-stu-id="ec585-105">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ec585-106">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="ec585-106">Attributes and elements</span></span>

<span data-ttu-id="ec585-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ec585-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ec585-108">屬性</span><span class="sxs-lookup"><span data-stu-id="ec585-108">Attributes</span></span>

<span data-ttu-id="ec585-109">無。</span><span class="sxs-lookup"><span data-stu-id="ec585-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ec585-110">子元素</span><span class="sxs-lookup"><span data-stu-id="ec585-110">Child elements</span></span>

<span data-ttu-id="ec585-111">項目</span><span class="sxs-lookup"><span data-stu-id="ec585-111">Element</span></span>  |<span data-ttu-id="ec585-112">說明</span><span class="sxs-lookup"><span data-stu-id="ec585-112">Description</span></span> |
---------|---------|
[`<add>`](windows-forms-add-configuration-element.md) | <span data-ttu-id="ec585-113">新增具有指定值的組態設定金鑰</span><span class="sxs-lookup"><span data-stu-id="ec585-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="ec585-114">父元素</span><span class="sxs-lookup"><span data-stu-id="ec585-114">Parent elements</span></span>

<span data-ttu-id="ec585-115">元素</span><span class="sxs-lookup"><span data-stu-id="ec585-115">Element</span></span>  |<span data-ttu-id="ec585-116">描述</span><span class="sxs-lookup"><span data-stu-id="ec585-116">Description</span></span> |
---------|---------|
[<span data-ttu-id="ec585-117">\<configuration></span><span class="sxs-lookup"><span data-stu-id="ec585-117">\<configuration></span></span>](../configuration-element.md) | <span data-ttu-id="ec585-118">通用語言執行平台和 Windows Forms 應用程式所使用之每個組態檔中的根元素</span><span class="sxs-lookup"><span data-stu-id="ec585-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="ec585-119">備註</span><span class="sxs-lookup"><span data-stu-id="ec585-119">Remarks</span></span>

<span data-ttu-id="ec585-120">從 .NET Framework 4.7 開始，`<System.Windows.Forms.ApplicationConfigurationSection>` 元素能允許您設定 Windows Forms 應用程式，以利用 .NET Framework 最新版本中的新增功能。</span><span class="sxs-lookup"><span data-stu-id="ec585-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span> 

<span data-ttu-id="ec585-121">`<System.Windows.Forms.ApplicationConfigurationSection>` 元素可以包含一或多個子 [`<add>`](windows-forms-add-configuration-element.md) 元素，每個子元素都能定義一個特定的組態設定。</span><span class="sxs-lookup"><span data-stu-id="ec585-121">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec585-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec585-122">See also</span></span>

- [<span data-ttu-id="ec585-123">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="ec585-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ec585-124">Windows Forms 中的高 DPI 支援</span><span class="sxs-lookup"><span data-stu-id="ec585-124">High DPI Support in Windows Forms</span></span>](../../../winforms/high-dpi-support-in-windows-forms.md)
