---
title: OLE DB 結構描述集合
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 2d5718c12100ebea49a6b6fab29a3790918c6ad3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783444"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="1f9f2-102">OLE DB 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="1f9f2-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="1f9f2-103">本節將討論 Microsoft SQL Server、Oracle 和 Microsoft Jet 之 OLE DB 提供者的結構描述集合支援。</span><span class="sxs-lookup"><span data-stu-id="1f9f2-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="1f9f2-104">Microsoft SQL Server OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="1f9f2-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="1f9f2-105">除了通用架構集合之外，Microsoft SQL Server OLE DB 驅動程式還支援下列特定的架構集合：</span><span class="sxs-lookup"><span data-stu-id="1f9f2-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="1f9f2-106">資料表</span><span class="sxs-lookup"><span data-stu-id="1f9f2-106">Tables</span></span>  
  
- <span data-ttu-id="1f9f2-107">資料行</span><span class="sxs-lookup"><span data-stu-id="1f9f2-107">Columns</span></span>  
  
- <span data-ttu-id="1f9f2-108">程序</span><span class="sxs-lookup"><span data-stu-id="1f9f2-108">Procedures</span></span>  
  
- <span data-ttu-id="1f9f2-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="1f9f2-109">ProcedureParameters</span></span>  
  
- <span data-ttu-id="1f9f2-110">Catalog</span><span class="sxs-lookup"><span data-stu-id="1f9f2-110">Catalog</span></span>  
  
- <span data-ttu-id="1f9f2-111">索引</span><span class="sxs-lookup"><span data-stu-id="1f9f2-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="1f9f2-112">資料表</span><span class="sxs-lookup"><span data-stu-id="1f9f2-112">Tables</span></span>  
  
|<span data-ttu-id="1f9f2-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="1f9f2-113">ColumnName</span></span>|<span data-ttu-id="1f9f2-114">DataType</span><span class="sxs-lookup"><span data-stu-id="1f9f2-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1f9f2-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-115">TABLE_CATALOG</span></span>|<span data-ttu-id="1f9f2-116">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-116">String</span></span>|  
|<span data-ttu-id="1f9f2-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="1f9f2-118">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-118">String</span></span>|  
|<span data-ttu-id="1f9f2-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-119">TABLE_NAME</span></span>|<span data-ttu-id="1f9f2-120">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-120">String</span></span>|  
|<span data-ttu-id="1f9f2-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-121">TABLE_TYPE</span></span>|<span data-ttu-id="1f9f2-122">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-122">String</span></span>|  
|<span data-ttu-id="1f9f2-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-123">TABLE_GUID</span></span>|<span data-ttu-id="1f9f2-124">Guid</span><span class="sxs-lookup"><span data-stu-id="1f9f2-124">Guid</span></span>|  
|<span data-ttu-id="1f9f2-125">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-125">DESCRIPTION</span></span>|<span data-ttu-id="1f9f2-126">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-126">String</span></span>|  
|<span data-ttu-id="1f9f2-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-127">TABLE_PROPID</span></span>|<span data-ttu-id="1f9f2-128">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-128">Int64</span></span>|  
|<span data-ttu-id="1f9f2-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="1f9f2-129">DATE_CREATED</span></span>|<span data-ttu-id="1f9f2-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="1f9f2-130">DateTime</span></span>|  
|<span data-ttu-id="1f9f2-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="1f9f2-131">DATE_MODIFIED</span></span>|<span data-ttu-id="1f9f2-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="1f9f2-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="1f9f2-133">資料行</span><span class="sxs-lookup"><span data-stu-id="1f9f2-133">Columns</span></span>  
  
|<span data-ttu-id="1f9f2-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="1f9f2-134">ColumnName</span></span>|<span data-ttu-id="1f9f2-135">DataType</span><span class="sxs-lookup"><span data-stu-id="1f9f2-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1f9f2-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-136">TABLE_CATALOG</span></span>|<span data-ttu-id="1f9f2-137">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-137">String</span></span>|  
|<span data-ttu-id="1f9f2-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="1f9f2-139">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-139">String</span></span>|  
|<span data-ttu-id="1f9f2-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-140">TABLE_NAME</span></span>|<span data-ttu-id="1f9f2-141">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-141">String</span></span>|  
|<span data-ttu-id="1f9f2-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-142">COLUMN_NAME</span></span>|<span data-ttu-id="1f9f2-143">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-143">String</span></span>|  
|<span data-ttu-id="1f9f2-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-144">COLUMN_GUID</span></span>|<span data-ttu-id="1f9f2-145">Guid</span><span class="sxs-lookup"><span data-stu-id="1f9f2-145">Guid</span></span>|  
|<span data-ttu-id="1f9f2-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-146">COLUMN_PROPID</span></span>|<span data-ttu-id="1f9f2-147">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-147">Int64</span></span>|  
|<span data-ttu-id="1f9f2-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="1f9f2-149">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-149">Int64</span></span>|  
|<span data-ttu-id="1f9f2-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="1f9f2-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="1f9f2-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-151">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="1f9f2-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="1f9f2-153">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-153">String</span></span>|  
|<span data-ttu-id="1f9f2-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="1f9f2-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="1f9f2-155">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-155">Int64</span></span>|  
|<span data-ttu-id="1f9f2-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-156">IS_NULLABLE</span></span>|<span data-ttu-id="1f9f2-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-157">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-158">DATA_TYPE</span></span>|<span data-ttu-id="1f9f2-159">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-159">Int32</span></span>|  
|<span data-ttu-id="1f9f2-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-160">TYPE_GUID</span></span>|<span data-ttu-id="1f9f2-161">Guid</span><span class="sxs-lookup"><span data-stu-id="1f9f2-161">Guid</span></span>|  
|<span data-ttu-id="1f9f2-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1f9f2-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="1f9f2-163">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-163">Int64</span></span>|  
|<span data-ttu-id="1f9f2-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1f9f2-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="1f9f2-165">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-165">Int64</span></span>|  
|<span data-ttu-id="1f9f2-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="1f9f2-167">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-167">Int32</span></span>|  
|<span data-ttu-id="1f9f2-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="1f9f2-169">Int16</span><span class="sxs-lookup"><span data-stu-id="1f9f2-169">Int16</span></span>|  
|<span data-ttu-id="1f9f2-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="1f9f2-171">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-171">Int64</span></span>|  
|<span data-ttu-id="1f9f2-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="1f9f2-173">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-173">String</span></span>|  
|<span data-ttu-id="1f9f2-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="1f9f2-175">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-175">String</span></span>|  
|<span data-ttu-id="1f9f2-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="1f9f2-177">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-177">String</span></span>|  
|<span data-ttu-id="1f9f2-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="1f9f2-179">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-179">String</span></span>|  
|<span data-ttu-id="1f9f2-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="1f9f2-181">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-181">String</span></span>|  
|<span data-ttu-id="1f9f2-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-182">COLLATION_NAME</span></span>|<span data-ttu-id="1f9f2-183">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-183">String</span></span>|  
|<span data-ttu-id="1f9f2-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="1f9f2-185">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-185">String</span></span>|  
|<span data-ttu-id="1f9f2-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="1f9f2-187">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-187">String</span></span>|  
|<span data-ttu-id="1f9f2-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-188">DOMAIN_NAME</span></span>|<span data-ttu-id="1f9f2-189">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-189">String</span></span>|  
|<span data-ttu-id="1f9f2-190">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-190">DESCRIPTION</span></span>|<span data-ttu-id="1f9f2-191">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-191">String</span></span>|  
|<span data-ttu-id="1f9f2-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-192">COLUMN_LCID</span></span>|<span data-ttu-id="1f9f2-193">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-193">Int32</span></span>|  
|<span data-ttu-id="1f9f2-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="1f9f2-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="1f9f2-195">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-195">Int32</span></span>|  
|<span data-ttu-id="1f9f2-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-196">COLUMN_SORTID</span></span>|<span data-ttu-id="1f9f2-197">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-197">Int32</span></span>|  
|<span data-ttu-id="1f9f2-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="1f9f2-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="1f9f2-199">Byte[]</span></span>|  
|<span data-ttu-id="1f9f2-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="1f9f2-200">IS_COMPUTED</span></span>|<span data-ttu-id="1f9f2-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="1f9f2-202">程序</span><span class="sxs-lookup"><span data-stu-id="1f9f2-202">Procedures</span></span>  
  
|<span data-ttu-id="1f9f2-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="1f9f2-203">ColumnName</span></span>|<span data-ttu-id="1f9f2-204">DataType</span><span class="sxs-lookup"><span data-stu-id="1f9f2-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1f9f2-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="1f9f2-206">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-206">String</span></span>|  
|<span data-ttu-id="1f9f2-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="1f9f2-208">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-208">String</span></span>|  
|<span data-ttu-id="1f9f2-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="1f9f2-210">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-210">String</span></span>|  
|<span data-ttu-id="1f9f2-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="1f9f2-212">Int16</span><span class="sxs-lookup"><span data-stu-id="1f9f2-212">Int16</span></span>|  
|<span data-ttu-id="1f9f2-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="1f9f2-214">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-214">String</span></span>|  
|<span data-ttu-id="1f9f2-215">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-215">DESCRIPTION</span></span>|<span data-ttu-id="1f9f2-216">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-216">String</span></span>|  
|<span data-ttu-id="1f9f2-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="1f9f2-217">DATE_CREATED</span></span>|<span data-ttu-id="1f9f2-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="1f9f2-218">DateTime</span></span>|  
|<span data-ttu-id="1f9f2-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="1f9f2-219">DATE_MODIFIED</span></span>|<span data-ttu-id="1f9f2-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="1f9f2-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="1f9f2-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="1f9f2-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="1f9f2-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="1f9f2-222">ColumnName</span></span>|<span data-ttu-id="1f9f2-223">DataType</span><span class="sxs-lookup"><span data-stu-id="1f9f2-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1f9f2-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="1f9f2-225">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-225">String</span></span>|  
|<span data-ttu-id="1f9f2-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="1f9f2-227">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-227">String</span></span>|  
|<span data-ttu-id="1f9f2-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="1f9f2-229">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-229">String</span></span>|  
|<span data-ttu-id="1f9f2-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-230">PARAMETER_NAME</span></span>|<span data-ttu-id="1f9f2-231">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-231">String</span></span>|  
|<span data-ttu-id="1f9f2-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="1f9f2-233">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-233">Int32</span></span>|  
|<span data-ttu-id="1f9f2-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="1f9f2-235">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-235">Int32</span></span>|  
|<span data-ttu-id="1f9f2-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="1f9f2-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="1f9f2-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-237">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="1f9f2-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="1f9f2-239">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-239">String</span></span>|  
|<span data-ttu-id="1f9f2-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-240">IS_NULLABLE</span></span>|<span data-ttu-id="1f9f2-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-241">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-242">DATA_TYPE</span></span>|<span data-ttu-id="1f9f2-243">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-243">Int32</span></span>|  
|<span data-ttu-id="1f9f2-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1f9f2-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="1f9f2-245">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-245">Int64</span></span>|  
|<span data-ttu-id="1f9f2-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1f9f2-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="1f9f2-247">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-247">Int64</span></span>|  
|<span data-ttu-id="1f9f2-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="1f9f2-249">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-249">Int32</span></span>|  
|<span data-ttu-id="1f9f2-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="1f9f2-251">Int16</span><span class="sxs-lookup"><span data-stu-id="1f9f2-251">Int16</span></span>|  
|<span data-ttu-id="1f9f2-252">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-252">DESCRIPTION</span></span>|<span data-ttu-id="1f9f2-253">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-253">String</span></span>|  
|<span data-ttu-id="1f9f2-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-254">TYPE_NAME</span></span>|<span data-ttu-id="1f9f2-255">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-255">String</span></span>|  
|<span data-ttu-id="1f9f2-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="1f9f2-257">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="1f9f2-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="1f9f2-258">Catalog</span></span>  
  
|<span data-ttu-id="1f9f2-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="1f9f2-259">ColumnName</span></span>|<span data-ttu-id="1f9f2-260">DataType</span><span class="sxs-lookup"><span data-stu-id="1f9f2-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1f9f2-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-261">CATALOG_NAME</span></span>|<span data-ttu-id="1f9f2-262">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-262">String</span></span>|  
|<span data-ttu-id="1f9f2-263">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-263">DESCRIPTION</span></span>|<span data-ttu-id="1f9f2-264">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="1f9f2-265">索引</span><span class="sxs-lookup"><span data-stu-id="1f9f2-265">Indexes</span></span>  
  
|<span data-ttu-id="1f9f2-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="1f9f2-266">ColumnName</span></span>|<span data-ttu-id="1f9f2-267">DataType</span><span class="sxs-lookup"><span data-stu-id="1f9f2-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1f9f2-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-268">TABLE_CATALOG</span></span>|<span data-ttu-id="1f9f2-269">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-269">String</span></span>|  
|<span data-ttu-id="1f9f2-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="1f9f2-271">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-271">String</span></span>|  
|<span data-ttu-id="1f9f2-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-272">TABLE_NAME</span></span>|<span data-ttu-id="1f9f2-273">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-273">String</span></span>|  
|<span data-ttu-id="1f9f2-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-274">INDEX_CATALOG</span></span>|<span data-ttu-id="1f9f2-275">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-275">String</span></span>|  
|<span data-ttu-id="1f9f2-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="1f9f2-277">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-277">String</span></span>|  
|<span data-ttu-id="1f9f2-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-278">INDEX_NAME</span></span>|<span data-ttu-id="1f9f2-279">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-279">String</span></span>|  
|<span data-ttu-id="1f9f2-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="1f9f2-280">PRIMARY_KEY</span></span>|<span data-ttu-id="1f9f2-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-281">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-282">UNIQUE</span></span>|<span data-ttu-id="1f9f2-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-283">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="1f9f2-284">CLUSTERED</span></span>|<span data-ttu-id="1f9f2-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-285">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-286">類型</span><span class="sxs-lookup"><span data-stu-id="1f9f2-286">TYPE</span></span>|<span data-ttu-id="1f9f2-287">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-287">Int32</span></span>|  
|<span data-ttu-id="1f9f2-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="1f9f2-288">FILL_FACTOR</span></span>|<span data-ttu-id="1f9f2-289">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-289">Int32</span></span>|  
|<span data-ttu-id="1f9f2-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-290">INITIAL_SIZE</span></span>|<span data-ttu-id="1f9f2-291">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-291">Int32</span></span>|  
|<span data-ttu-id="1f9f2-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="1f9f2-292">NULLS</span></span>|<span data-ttu-id="1f9f2-293">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-293">Int32</span></span>|  
|<span data-ttu-id="1f9f2-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="1f9f2-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="1f9f2-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-295">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-296">AUTO_UPDATE</span></span>|<span data-ttu-id="1f9f2-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-297">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-298">NULL_COLLATION</span></span>|<span data-ttu-id="1f9f2-299">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-299">Int32</span></span>|  
|<span data-ttu-id="1f9f2-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="1f9f2-301">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-301">Int64</span></span>|  
|<span data-ttu-id="1f9f2-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-302">COLUMN_NAME</span></span>|<span data-ttu-id="1f9f2-303">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-303">String</span></span>|  
|<span data-ttu-id="1f9f2-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-304">COLUMN_GUID</span></span>|<span data-ttu-id="1f9f2-305">Guid</span><span class="sxs-lookup"><span data-stu-id="1f9f2-305">Guid</span></span>|  
|<span data-ttu-id="1f9f2-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-306">COLUMN_PROPID</span></span>|<span data-ttu-id="1f9f2-307">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-307">Int64</span></span>|  
|<span data-ttu-id="1f9f2-308">COLLATION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-308">COLLATION</span></span>|<span data-ttu-id="1f9f2-309">Int16</span><span class="sxs-lookup"><span data-stu-id="1f9f2-309">Int16</span></span>|  
|<span data-ttu-id="1f9f2-310">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="1f9f2-310">CARDINALITY</span></span>|<span data-ttu-id="1f9f2-311">Decimal</span><span class="sxs-lookup"><span data-stu-id="1f9f2-311">Decimal</span></span>|  
|<span data-ttu-id="1f9f2-312">PAGES</span><span class="sxs-lookup"><span data-stu-id="1f9f2-312">PAGES</span></span>|<span data-ttu-id="1f9f2-313">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-313">Int32</span></span>|  
|<span data-ttu-id="1f9f2-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-314">FILTER_CONDITION</span></span>|<span data-ttu-id="1f9f2-315">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-315">String</span></span>|  
|<span data-ttu-id="1f9f2-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="1f9f2-316">INTEGRATED</span></span>|<span data-ttu-id="1f9f2-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="1f9f2-318">Microsoft Oracle OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="1f9f2-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="1f9f2-319">除了通用結構描述集合之外，Microsoft Oracle OLE DB 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="1f9f2-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="1f9f2-320">資料表</span><span class="sxs-lookup"><span data-stu-id="1f9f2-320">Tables</span></span>  
  
- <span data-ttu-id="1f9f2-321">資料行</span><span class="sxs-lookup"><span data-stu-id="1f9f2-321">Columns</span></span>  
  
- <span data-ttu-id="1f9f2-322">程序</span><span class="sxs-lookup"><span data-stu-id="1f9f2-322">Procedures</span></span>  
  
- <span data-ttu-id="1f9f2-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="1f9f2-323">ProcedureColumns</span></span>  
  
- <span data-ttu-id="1f9f2-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="1f9f2-324">ProcedureParameters</span></span>  
  
- <span data-ttu-id="1f9f2-325">檢視</span><span class="sxs-lookup"><span data-stu-id="1f9f2-325">Views</span></span>  
  
- <span data-ttu-id="1f9f2-326">索引</span><span class="sxs-lookup"><span data-stu-id="1f9f2-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="1f9f2-327">資料表</span><span class="sxs-lookup"><span data-stu-id="1f9f2-327">Tables</span></span>  
  
|<span data-ttu-id="1f9f2-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="1f9f2-328">ColumnName</span></span>|<span data-ttu-id="1f9f2-329">DataType</span><span class="sxs-lookup"><span data-stu-id="1f9f2-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1f9f2-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-330">TABLE_CATALOG</span></span>|<span data-ttu-id="1f9f2-331">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-331">String</span></span>|  
|<span data-ttu-id="1f9f2-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="1f9f2-333">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-333">String</span></span>|  
|<span data-ttu-id="1f9f2-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-334">TABLE_NAME</span></span>|<span data-ttu-id="1f9f2-335">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-335">String</span></span>|  
|<span data-ttu-id="1f9f2-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-336">TABLE_TYPE</span></span>|<span data-ttu-id="1f9f2-337">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-337">String</span></span>|  
|<span data-ttu-id="1f9f2-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-338">TABLE_GUID</span></span>|<span data-ttu-id="1f9f2-339">Guid</span><span class="sxs-lookup"><span data-stu-id="1f9f2-339">Guid</span></span>|  
|<span data-ttu-id="1f9f2-340">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-340">DESCRIPTION</span></span>|<span data-ttu-id="1f9f2-341">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-341">String</span></span>|  
|<span data-ttu-id="1f9f2-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-342">TABLE_PROPID</span></span>|<span data-ttu-id="1f9f2-343">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-343">Int64</span></span>|  
|<span data-ttu-id="1f9f2-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="1f9f2-344">DATE_CREATED</span></span>|<span data-ttu-id="1f9f2-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="1f9f2-345">DateTime</span></span>|  
|<span data-ttu-id="1f9f2-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="1f9f2-346">DATE_MODIFIED</span></span>|<span data-ttu-id="1f9f2-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="1f9f2-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="1f9f2-348">資料行</span><span class="sxs-lookup"><span data-stu-id="1f9f2-348">Columns</span></span>  
  
|<span data-ttu-id="1f9f2-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="1f9f2-349">ColumnName</span></span>|<span data-ttu-id="1f9f2-350">DataType</span><span class="sxs-lookup"><span data-stu-id="1f9f2-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1f9f2-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-351">TABLE_CATALOG</span></span>|<span data-ttu-id="1f9f2-352">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-352">String</span></span>|  
|<span data-ttu-id="1f9f2-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="1f9f2-354">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-354">String</span></span>|  
|<span data-ttu-id="1f9f2-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-355">TABLE_NAME</span></span>|<span data-ttu-id="1f9f2-356">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-356">String</span></span>|  
|<span data-ttu-id="1f9f2-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-357">COLUMN_NAME</span></span>|<span data-ttu-id="1f9f2-358">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-358">String</span></span>|  
|<span data-ttu-id="1f9f2-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-359">COLUMN_GUID</span></span>|<span data-ttu-id="1f9f2-360">Guid</span><span class="sxs-lookup"><span data-stu-id="1f9f2-360">Guid</span></span>|  
|<span data-ttu-id="1f9f2-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-361">COLUMN_PROPID</span></span>|<span data-ttu-id="1f9f2-362">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-362">Int64</span></span>|  
|<span data-ttu-id="1f9f2-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="1f9f2-364">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-364">Int64</span></span>|  
|<span data-ttu-id="1f9f2-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="1f9f2-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="1f9f2-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-366">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="1f9f2-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="1f9f2-368">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-368">String</span></span>|  
|<span data-ttu-id="1f9f2-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="1f9f2-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="1f9f2-370">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-370">Int64</span></span>|  
|<span data-ttu-id="1f9f2-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-371">IS_NULLABLE</span></span>|<span data-ttu-id="1f9f2-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-372">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-373">DATA_TYPE</span></span>|<span data-ttu-id="1f9f2-374">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-374">Int32</span></span>|  
|<span data-ttu-id="1f9f2-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-375">TYPE_GUID</span></span>|<span data-ttu-id="1f9f2-376">Guid</span><span class="sxs-lookup"><span data-stu-id="1f9f2-376">Guid</span></span>|  
|<span data-ttu-id="1f9f2-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1f9f2-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="1f9f2-378">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-378">Int64</span></span>|  
|<span data-ttu-id="1f9f2-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1f9f2-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="1f9f2-380">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-380">Int64</span></span>|  
|<span data-ttu-id="1f9f2-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="1f9f2-382">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-382">Int32</span></span>|  
|<span data-ttu-id="1f9f2-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="1f9f2-384">Int16</span><span class="sxs-lookup"><span data-stu-id="1f9f2-384">Int16</span></span>|  
|<span data-ttu-id="1f9f2-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="1f9f2-386">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-386">Int64</span></span>|  
|<span data-ttu-id="1f9f2-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="1f9f2-388">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-388">String</span></span>|  
|<span data-ttu-id="1f9f2-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="1f9f2-390">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-390">String</span></span>|  
|<span data-ttu-id="1f9f2-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="1f9f2-392">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-392">String</span></span>|  
|<span data-ttu-id="1f9f2-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="1f9f2-394">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-394">String</span></span>|  
|<span data-ttu-id="1f9f2-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="1f9f2-396">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-396">String</span></span>|  
|<span data-ttu-id="1f9f2-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-397">COLLATION_NAME</span></span>|<span data-ttu-id="1f9f2-398">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-398">String</span></span>|  
|<span data-ttu-id="1f9f2-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="1f9f2-400">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-400">String</span></span>|  
|<span data-ttu-id="1f9f2-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="1f9f2-402">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-402">String</span></span>|  
|<span data-ttu-id="1f9f2-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-403">DOMAIN_NAME</span></span>|<span data-ttu-id="1f9f2-404">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-404">String</span></span>|  
|<span data-ttu-id="1f9f2-405">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-405">DESCRIPTION</span></span>|<span data-ttu-id="1f9f2-406">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="1f9f2-407">程序</span><span class="sxs-lookup"><span data-stu-id="1f9f2-407">Procedures</span></span>  
  
|<span data-ttu-id="1f9f2-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="1f9f2-408">ColumnName</span></span>|<span data-ttu-id="1f9f2-409">DataType</span><span class="sxs-lookup"><span data-stu-id="1f9f2-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1f9f2-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="1f9f2-411">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-411">String</span></span>|  
|<span data-ttu-id="1f9f2-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="1f9f2-413">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-413">String</span></span>|  
|<span data-ttu-id="1f9f2-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="1f9f2-415">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-415">String</span></span>|  
|<span data-ttu-id="1f9f2-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="1f9f2-417">Int16</span><span class="sxs-lookup"><span data-stu-id="1f9f2-417">Int16</span></span>|  
|<span data-ttu-id="1f9f2-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="1f9f2-419">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-419">String</span></span>|  
|<span data-ttu-id="1f9f2-420">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-420">DESCRIPTION</span></span>|<span data-ttu-id="1f9f2-421">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-421">String</span></span>|  
|<span data-ttu-id="1f9f2-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="1f9f2-422">DATE_CREATED</span></span>|<span data-ttu-id="1f9f2-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="1f9f2-423">DateTime</span></span>|  
|<span data-ttu-id="1f9f2-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="1f9f2-424">DATE_MODIFIED</span></span>|<span data-ttu-id="1f9f2-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="1f9f2-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="1f9f2-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="1f9f2-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="1f9f2-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="1f9f2-427">ColumnName</span></span>|<span data-ttu-id="1f9f2-428">DataType</span><span class="sxs-lookup"><span data-stu-id="1f9f2-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1f9f2-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="1f9f2-430">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-430">String</span></span>|  
|<span data-ttu-id="1f9f2-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="1f9f2-432">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-432">String</span></span>|  
|<span data-ttu-id="1f9f2-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="1f9f2-434">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-434">String</span></span>|  
|<span data-ttu-id="1f9f2-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-435">COLUMN_NAME</span></span>|<span data-ttu-id="1f9f2-436">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-436">String</span></span>|  
|<span data-ttu-id="1f9f2-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-437">COLUMN_GUID</span></span>|<span data-ttu-id="1f9f2-438">Guid</span><span class="sxs-lookup"><span data-stu-id="1f9f2-438">Guid</span></span>|  
|<span data-ttu-id="1f9f2-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-439">COLUMN_PROPID</span></span>|<span data-ttu-id="1f9f2-440">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-440">Int64</span></span>|  
|<span data-ttu-id="1f9f2-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="1f9f2-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="1f9f2-442">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-442">Int64</span></span>|  
|<span data-ttu-id="1f9f2-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="1f9f2-444">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-444">Int64</span></span>|  
|<span data-ttu-id="1f9f2-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-445">IS_NULLABLE</span></span>|<span data-ttu-id="1f9f2-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-446">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-447">DATA_TYPE</span></span>|<span data-ttu-id="1f9f2-448">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-448">Int32</span></span>|  
|<span data-ttu-id="1f9f2-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-449">TYPE_GUID</span></span>|<span data-ttu-id="1f9f2-450">Guid</span><span class="sxs-lookup"><span data-stu-id="1f9f2-450">Guid</span></span>|  
|<span data-ttu-id="1f9f2-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1f9f2-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="1f9f2-452">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-452">Int64</span></span>|  
|<span data-ttu-id="1f9f2-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1f9f2-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="1f9f2-454">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-454">Int64</span></span>|  
|<span data-ttu-id="1f9f2-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="1f9f2-456">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-456">Int32</span></span>|  
|<span data-ttu-id="1f9f2-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="1f9f2-458">Int16</span><span class="sxs-lookup"><span data-stu-id="1f9f2-458">Int16</span></span>|  
|<span data-ttu-id="1f9f2-459">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-459">DESCRIPTION</span></span>|<span data-ttu-id="1f9f2-460">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-460">String</span></span>|  
|<span data-ttu-id="1f9f2-461">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="1f9f2-461">OVERLOAD</span></span>|<span data-ttu-id="1f9f2-462">Int16</span><span class="sxs-lookup"><span data-stu-id="1f9f2-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="1f9f2-463">檢視</span><span class="sxs-lookup"><span data-stu-id="1f9f2-463">Views</span></span>  
  
|<span data-ttu-id="1f9f2-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="1f9f2-464">ColumnName</span></span>|<span data-ttu-id="1f9f2-465">DataType</span><span class="sxs-lookup"><span data-stu-id="1f9f2-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1f9f2-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-466">TABLE_CATALOG</span></span>|<span data-ttu-id="1f9f2-467">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-467">String</span></span>|  
|<span data-ttu-id="1f9f2-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="1f9f2-469">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-469">String</span></span>|  
|<span data-ttu-id="1f9f2-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-470">TABLE_NAME</span></span>|<span data-ttu-id="1f9f2-471">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-471">String</span></span>|  
|<span data-ttu-id="1f9f2-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="1f9f2-473">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-473">String</span></span>|  
|<span data-ttu-id="1f9f2-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-474">CHECK_OPTION</span></span>|<span data-ttu-id="1f9f2-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-475">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-476">IS_UPDATABLE</span></span>|<span data-ttu-id="1f9f2-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-477">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-478">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-478">DESCRIPTION</span></span>|<span data-ttu-id="1f9f2-479">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-479">String</span></span>|  
|<span data-ttu-id="1f9f2-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="1f9f2-480">DATE_CREATED</span></span>|<span data-ttu-id="1f9f2-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="1f9f2-481">DateTime</span></span>|  
|<span data-ttu-id="1f9f2-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="1f9f2-482">DATE_MODIFIED</span></span>|<span data-ttu-id="1f9f2-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="1f9f2-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="1f9f2-484">索引</span><span class="sxs-lookup"><span data-stu-id="1f9f2-484">Indexes</span></span>  
  
|<span data-ttu-id="1f9f2-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="1f9f2-485">ColumnName</span></span>|<span data-ttu-id="1f9f2-486">DataType</span><span class="sxs-lookup"><span data-stu-id="1f9f2-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1f9f2-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-487">TABLE_CATALOG</span></span>|<span data-ttu-id="1f9f2-488">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-488">String</span></span>|  
|<span data-ttu-id="1f9f2-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="1f9f2-490">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-490">String</span></span>|  
|<span data-ttu-id="1f9f2-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-491">TABLE_NAME</span></span>|<span data-ttu-id="1f9f2-492">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-492">String</span></span>|  
|<span data-ttu-id="1f9f2-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-493">INDEX_CATALOG</span></span>|<span data-ttu-id="1f9f2-494">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-494">String</span></span>|  
|<span data-ttu-id="1f9f2-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="1f9f2-496">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-496">String</span></span>|  
|<span data-ttu-id="1f9f2-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-497">INDEX_NAME</span></span>|<span data-ttu-id="1f9f2-498">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-498">String</span></span>|  
|<span data-ttu-id="1f9f2-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="1f9f2-499">PRIMARY_KEY</span></span>|<span data-ttu-id="1f9f2-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-500">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-501">UNIQUE</span></span>|<span data-ttu-id="1f9f2-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-502">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="1f9f2-503">CLUSTERED</span></span>|<span data-ttu-id="1f9f2-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-504">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-505">類型</span><span class="sxs-lookup"><span data-stu-id="1f9f2-505">TYPE</span></span>|<span data-ttu-id="1f9f2-506">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-506">Int32</span></span>|  
|<span data-ttu-id="1f9f2-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="1f9f2-507">FILL_FACTOR</span></span>|<span data-ttu-id="1f9f2-508">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-508">Int32</span></span>|  
|<span data-ttu-id="1f9f2-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-509">INITIAL_SIZE</span></span>|<span data-ttu-id="1f9f2-510">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-510">Int32</span></span>|  
|<span data-ttu-id="1f9f2-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="1f9f2-511">NULLS</span></span>|<span data-ttu-id="1f9f2-512">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-512">Int32</span></span>|  
|<span data-ttu-id="1f9f2-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="1f9f2-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="1f9f2-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-514">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-515">AUTO_UPDATE</span></span>|<span data-ttu-id="1f9f2-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-516">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-517">NULL_COLLATION</span></span>|<span data-ttu-id="1f9f2-518">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-518">Int32</span></span>|  
|<span data-ttu-id="1f9f2-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="1f9f2-520">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-520">Int64</span></span>|  
|<span data-ttu-id="1f9f2-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-521">COLUMN_NAME</span></span>|<span data-ttu-id="1f9f2-522">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-522">String</span></span>|  
|<span data-ttu-id="1f9f2-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-523">COLUMN_GUID</span></span>|<span data-ttu-id="1f9f2-524">Guid</span><span class="sxs-lookup"><span data-stu-id="1f9f2-524">Guid</span></span>|  
|<span data-ttu-id="1f9f2-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-525">COLUMN_PROPID</span></span>|<span data-ttu-id="1f9f2-526">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-526">Int64</span></span>|  
|<span data-ttu-id="1f9f2-527">COLLATION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-527">COLLATION</span></span>|<span data-ttu-id="1f9f2-528">Int16</span><span class="sxs-lookup"><span data-stu-id="1f9f2-528">Int16</span></span>|  
|<span data-ttu-id="1f9f2-529">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="1f9f2-529">CARDINALITY</span></span>|<span data-ttu-id="1f9f2-530">Decimal</span><span class="sxs-lookup"><span data-stu-id="1f9f2-530">Decimal</span></span>|  
|<span data-ttu-id="1f9f2-531">PAGES</span><span class="sxs-lookup"><span data-stu-id="1f9f2-531">PAGES</span></span>|<span data-ttu-id="1f9f2-532">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-532">Int32</span></span>|  
|<span data-ttu-id="1f9f2-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-533">FILTER_CONDITION</span></span>|<span data-ttu-id="1f9f2-534">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-534">String</span></span>|  
|<span data-ttu-id="1f9f2-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="1f9f2-535">INTEGRATED</span></span>|<span data-ttu-id="1f9f2-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="1f9f2-537">Microsoft Jet OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="1f9f2-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="1f9f2-538">除了通用結構描述集合之外，Microsoft Jet OLE DB 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="1f9f2-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="1f9f2-539">資料表</span><span class="sxs-lookup"><span data-stu-id="1f9f2-539">Tables</span></span>  
  
- <span data-ttu-id="1f9f2-540">資料行</span><span class="sxs-lookup"><span data-stu-id="1f9f2-540">Columns</span></span>  
  
- <span data-ttu-id="1f9f2-541">程序</span><span class="sxs-lookup"><span data-stu-id="1f9f2-541">Procedures</span></span>  
  
- <span data-ttu-id="1f9f2-542">檢視</span><span class="sxs-lookup"><span data-stu-id="1f9f2-542">Views</span></span>  
  
- <span data-ttu-id="1f9f2-543">索引</span><span class="sxs-lookup"><span data-stu-id="1f9f2-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="1f9f2-544">資料表</span><span class="sxs-lookup"><span data-stu-id="1f9f2-544">Tables</span></span>  
  
|<span data-ttu-id="1f9f2-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="1f9f2-545">ColumnName</span></span>|<span data-ttu-id="1f9f2-546">DataType</span><span class="sxs-lookup"><span data-stu-id="1f9f2-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1f9f2-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-547">TABLE_CATALOG</span></span>|<span data-ttu-id="1f9f2-548">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-548">String</span></span>|  
|<span data-ttu-id="1f9f2-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="1f9f2-550">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-550">String</span></span>|  
|<span data-ttu-id="1f9f2-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-551">TABLE_NAME</span></span>|<span data-ttu-id="1f9f2-552">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-552">String</span></span>|  
|<span data-ttu-id="1f9f2-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-553">TABLE_TYPE</span></span>|<span data-ttu-id="1f9f2-554">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-554">String</span></span>|  
|<span data-ttu-id="1f9f2-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-555">TABLE_GUID</span></span>|<span data-ttu-id="1f9f2-556">Guid</span><span class="sxs-lookup"><span data-stu-id="1f9f2-556">Guid</span></span>|  
|<span data-ttu-id="1f9f2-557">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-557">DESCRIPTION</span></span>|<span data-ttu-id="1f9f2-558">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-558">String</span></span>|  
|<span data-ttu-id="1f9f2-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-559">TABLE_PROPID</span></span>|<span data-ttu-id="1f9f2-560">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-560">Int64</span></span>|  
|<span data-ttu-id="1f9f2-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="1f9f2-561">DATE_CREATED</span></span>|<span data-ttu-id="1f9f2-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="1f9f2-562">DateTime</span></span>|  
|<span data-ttu-id="1f9f2-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="1f9f2-563">DATE_MODIFIED</span></span>|<span data-ttu-id="1f9f2-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="1f9f2-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="1f9f2-565">資料行</span><span class="sxs-lookup"><span data-stu-id="1f9f2-565">Columns</span></span>  
  
|<span data-ttu-id="1f9f2-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="1f9f2-566">ColumnName</span></span>|<span data-ttu-id="1f9f2-567">DataType</span><span class="sxs-lookup"><span data-stu-id="1f9f2-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1f9f2-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-568">TABLE_CATALOG</span></span>|<span data-ttu-id="1f9f2-569">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-569">String</span></span>|  
|<span data-ttu-id="1f9f2-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="1f9f2-571">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-571">String</span></span>|  
|<span data-ttu-id="1f9f2-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-572">TABLE_NAME</span></span>|<span data-ttu-id="1f9f2-573">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-573">String</span></span>|  
|<span data-ttu-id="1f9f2-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-574">COLUMN_NAME</span></span>|<span data-ttu-id="1f9f2-575">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-575">String</span></span>|  
|<span data-ttu-id="1f9f2-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-576">COLUMN_GUID</span></span>|<span data-ttu-id="1f9f2-577">Guid</span><span class="sxs-lookup"><span data-stu-id="1f9f2-577">Guid</span></span>|  
|<span data-ttu-id="1f9f2-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-578">COLUMN_PROPID</span></span>|<span data-ttu-id="1f9f2-579">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-579">Int64</span></span>|  
|<span data-ttu-id="1f9f2-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="1f9f2-581">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-581">Int64</span></span>|  
|<span data-ttu-id="1f9f2-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="1f9f2-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="1f9f2-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-583">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="1f9f2-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="1f9f2-585">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-585">String</span></span>|  
|<span data-ttu-id="1f9f2-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="1f9f2-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="1f9f2-587">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-587">Int64</span></span>|  
|<span data-ttu-id="1f9f2-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-588">IS_NULLABLE</span></span>|<span data-ttu-id="1f9f2-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-589">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-590">DATA_TYPE</span></span>|<span data-ttu-id="1f9f2-591">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-591">Int32</span></span>|  
|<span data-ttu-id="1f9f2-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-592">TYPE_GUID</span></span>|<span data-ttu-id="1f9f2-593">Guid</span><span class="sxs-lookup"><span data-stu-id="1f9f2-593">Guid</span></span>|  
|<span data-ttu-id="1f9f2-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1f9f2-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="1f9f2-595">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-595">Int64</span></span>|  
|<span data-ttu-id="1f9f2-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="1f9f2-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="1f9f2-597">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-597">Int64</span></span>|  
|<span data-ttu-id="1f9f2-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="1f9f2-599">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-599">Int32</span></span>|  
|<span data-ttu-id="1f9f2-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="1f9f2-601">Int16</span><span class="sxs-lookup"><span data-stu-id="1f9f2-601">Int16</span></span>|  
|<span data-ttu-id="1f9f2-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="1f9f2-603">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-603">Int64</span></span>|  
|<span data-ttu-id="1f9f2-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="1f9f2-605">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-605">String</span></span>|  
|<span data-ttu-id="1f9f2-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="1f9f2-607">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-607">String</span></span>|  
|<span data-ttu-id="1f9f2-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="1f9f2-609">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-609">String</span></span>|  
|<span data-ttu-id="1f9f2-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="1f9f2-611">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-611">String</span></span>|  
|<span data-ttu-id="1f9f2-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="1f9f2-613">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-613">String</span></span>|  
|<span data-ttu-id="1f9f2-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-614">COLLATION_NAME</span></span>|<span data-ttu-id="1f9f2-615">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-615">String</span></span>|  
|<span data-ttu-id="1f9f2-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="1f9f2-617">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-617">String</span></span>|  
|<span data-ttu-id="1f9f2-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="1f9f2-619">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-619">String</span></span>|  
|<span data-ttu-id="1f9f2-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-620">DOMAIN_NAME</span></span>|<span data-ttu-id="1f9f2-621">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-621">String</span></span>|  
|<span data-ttu-id="1f9f2-622">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-622">DESCRIPTION</span></span>|<span data-ttu-id="1f9f2-623">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="1f9f2-624">程序</span><span class="sxs-lookup"><span data-stu-id="1f9f2-624">Procedures</span></span>  
  
|<span data-ttu-id="1f9f2-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="1f9f2-625">ColumnName</span></span>|<span data-ttu-id="1f9f2-626">DataType</span><span class="sxs-lookup"><span data-stu-id="1f9f2-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1f9f2-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="1f9f2-628">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-628">String</span></span>|  
|<span data-ttu-id="1f9f2-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="1f9f2-630">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-630">String</span></span>|  
|<span data-ttu-id="1f9f2-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="1f9f2-632">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-632">String</span></span>|  
|<span data-ttu-id="1f9f2-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="1f9f2-634">Int16</span><span class="sxs-lookup"><span data-stu-id="1f9f2-634">Int16</span></span>|  
|<span data-ttu-id="1f9f2-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="1f9f2-636">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-636">String</span></span>|  
|<span data-ttu-id="1f9f2-637">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-637">DESCRIPTION</span></span>|<span data-ttu-id="1f9f2-638">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-638">String</span></span>|  
|<span data-ttu-id="1f9f2-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="1f9f2-639">DATE_CREATED</span></span>|<span data-ttu-id="1f9f2-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="1f9f2-640">DateTime</span></span>|  
|<span data-ttu-id="1f9f2-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="1f9f2-641">DATE_MODIFIED</span></span>|<span data-ttu-id="1f9f2-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="1f9f2-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="1f9f2-643">檢視</span><span class="sxs-lookup"><span data-stu-id="1f9f2-643">Views</span></span>  
  
|<span data-ttu-id="1f9f2-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="1f9f2-644">ColumnName</span></span>|<span data-ttu-id="1f9f2-645">DataType</span><span class="sxs-lookup"><span data-stu-id="1f9f2-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1f9f2-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-646">TABLE_CATALOG</span></span>|<span data-ttu-id="1f9f2-647">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-647">String</span></span>|  
|<span data-ttu-id="1f9f2-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="1f9f2-649">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-649">String</span></span>|  
|<span data-ttu-id="1f9f2-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-650">TABLE_NAME</span></span>|<span data-ttu-id="1f9f2-651">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-651">String</span></span>|  
|<span data-ttu-id="1f9f2-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="1f9f2-653">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-653">String</span></span>|  
|<span data-ttu-id="1f9f2-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-654">CHECK_OPTION</span></span>|<span data-ttu-id="1f9f2-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-655">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-656">IS_UPDATABLE</span></span>|<span data-ttu-id="1f9f2-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-657">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-658">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-658">DESCRIPTION</span></span>|<span data-ttu-id="1f9f2-659">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-659">String</span></span>|  
|<span data-ttu-id="1f9f2-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="1f9f2-660">DATE_CREATED</span></span>|<span data-ttu-id="1f9f2-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="1f9f2-661">DateTime</span></span>|  
|<span data-ttu-id="1f9f2-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="1f9f2-662">DATE_MODIFIED</span></span>|<span data-ttu-id="1f9f2-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="1f9f2-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="1f9f2-664">索引</span><span class="sxs-lookup"><span data-stu-id="1f9f2-664">Indexes</span></span>  
  
|<span data-ttu-id="1f9f2-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="1f9f2-665">ColumnName</span></span>|<span data-ttu-id="1f9f2-666">DataType</span><span class="sxs-lookup"><span data-stu-id="1f9f2-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="1f9f2-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-667">TABLE_CATALOG</span></span>|<span data-ttu-id="1f9f2-668">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-668">String</span></span>|  
|<span data-ttu-id="1f9f2-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="1f9f2-670">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-670">String</span></span>|  
|<span data-ttu-id="1f9f2-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-671">TABLE_NAME</span></span>|<span data-ttu-id="1f9f2-672">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-672">String</span></span>|  
|<span data-ttu-id="1f9f2-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="1f9f2-673">INDEX_CATALOG</span></span>|<span data-ttu-id="1f9f2-674">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-674">String</span></span>|  
|<span data-ttu-id="1f9f2-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="1f9f2-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="1f9f2-676">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-676">String</span></span>|  
|<span data-ttu-id="1f9f2-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-677">INDEX_NAME</span></span>|<span data-ttu-id="1f9f2-678">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-678">String</span></span>|  
|<span data-ttu-id="1f9f2-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="1f9f2-679">PRIMARY_KEY</span></span>|<span data-ttu-id="1f9f2-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-680">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-681">UNIQUE</span></span>|<span data-ttu-id="1f9f2-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-682">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="1f9f2-683">CLUSTERED</span></span>|<span data-ttu-id="1f9f2-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-684">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-685">類型</span><span class="sxs-lookup"><span data-stu-id="1f9f2-685">TYPE</span></span>|<span data-ttu-id="1f9f2-686">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-686">Int32</span></span>|  
|<span data-ttu-id="1f9f2-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="1f9f2-687">FILL_FACTOR</span></span>|<span data-ttu-id="1f9f2-688">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-688">Int32</span></span>|  
|<span data-ttu-id="1f9f2-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-689">INITIAL_SIZE</span></span>|<span data-ttu-id="1f9f2-690">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-690">Int32</span></span>|  
|<span data-ttu-id="1f9f2-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="1f9f2-691">NULLS</span></span>|<span data-ttu-id="1f9f2-692">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-692">Int32</span></span>|  
|<span data-ttu-id="1f9f2-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="1f9f2-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="1f9f2-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-694">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="1f9f2-695">AUTO_UPDATE</span></span>|<span data-ttu-id="1f9f2-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-696">Boolean</span></span>|  
|<span data-ttu-id="1f9f2-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-697">NULL_COLLATION</span></span>|<span data-ttu-id="1f9f2-698">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-698">Int32</span></span>|  
|<span data-ttu-id="1f9f2-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="1f9f2-700">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-700">Int64</span></span>|  
|<span data-ttu-id="1f9f2-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="1f9f2-701">COLUMN_NAME</span></span>|<span data-ttu-id="1f9f2-702">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-702">String</span></span>|  
|<span data-ttu-id="1f9f2-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-703">COLUMN_GUID</span></span>|<span data-ttu-id="1f9f2-704">Guid</span><span class="sxs-lookup"><span data-stu-id="1f9f2-704">Guid</span></span>|  
|<span data-ttu-id="1f9f2-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="1f9f2-705">COLUMN_PROPID</span></span>|<span data-ttu-id="1f9f2-706">Int64</span><span class="sxs-lookup"><span data-stu-id="1f9f2-706">Int64</span></span>|  
|<span data-ttu-id="1f9f2-707">COLLATION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-707">COLLATION</span></span>|<span data-ttu-id="1f9f2-708">Int16</span><span class="sxs-lookup"><span data-stu-id="1f9f2-708">Int16</span></span>|  
|<span data-ttu-id="1f9f2-709">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="1f9f2-709">CARDINALITY</span></span>|<span data-ttu-id="1f9f2-710">Decimal</span><span class="sxs-lookup"><span data-stu-id="1f9f2-710">Decimal</span></span>|  
|<span data-ttu-id="1f9f2-711">PAGES</span><span class="sxs-lookup"><span data-stu-id="1f9f2-711">PAGES</span></span>|<span data-ttu-id="1f9f2-712">Int32</span><span class="sxs-lookup"><span data-stu-id="1f9f2-712">Int32</span></span>|  
|<span data-ttu-id="1f9f2-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="1f9f2-713">FILTER_CONDITION</span></span>|<span data-ttu-id="1f9f2-714">String</span><span class="sxs-lookup"><span data-stu-id="1f9f2-714">String</span></span>|  
|<span data-ttu-id="1f9f2-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="1f9f2-715">INTEGRATED</span></span>|<span data-ttu-id="1f9f2-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="1f9f2-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1f9f2-717">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f9f2-717">See also</span></span>

- [<span data-ttu-id="1f9f2-718">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="1f9f2-718">ADO.NET Overview</span></span>](ado-net-overview.md)
