---
title: ODBC 結構描述集合
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: ffe80120ceffbe29c0a117cf1194860c5782be8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772043"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="4b8e0-102">ODBC 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="4b8e0-102">ODBC Schema Collections</span></span>

<span data-ttu-id="4b8e0-103">本節將討論 Microsoft SQL Server、Oracle 和 Microsoft Jet 之 ODBC 驅動程式的結構描述集合支援。</span><span class="sxs-lookup"><span data-stu-id="4b8e0-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>

## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="4b8e0-104">Microsoft SQL Server ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="4b8e0-104">Microsoft SQL Server ODBC Driver</span></span>

<span data-ttu-id="4b8e0-105">Microsoft SQL Server ODBC 驅動程式支援下列特定結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="4b8e0-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="4b8e0-106">資料表</span><span class="sxs-lookup"><span data-stu-id="4b8e0-106">Tables</span></span>

- <span data-ttu-id="4b8e0-107">索引</span><span class="sxs-lookup"><span data-stu-id="4b8e0-107">Indexes</span></span>

- <span data-ttu-id="4b8e0-108">資料行</span><span class="sxs-lookup"><span data-stu-id="4b8e0-108">Columns</span></span>

- <span data-ttu-id="4b8e0-109">程序</span><span class="sxs-lookup"><span data-stu-id="4b8e0-109">Procedures</span></span>

- <span data-ttu-id="4b8e0-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="4b8e0-110">ProcedureColumns</span></span>

- <span data-ttu-id="4b8e0-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="4b8e0-111">ProcedureParameters</span></span>

- <span data-ttu-id="4b8e0-112">檢視</span><span class="sxs-lookup"><span data-stu-id="4b8e0-112">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="4b8e0-113">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="4b8e0-113">Tables and Views</span></span>

|<span data-ttu-id="4b8e0-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4b8e0-114">ColumnName</span></span>|<span data-ttu-id="4b8e0-115">DataType</span><span class="sxs-lookup"><span data-stu-id="4b8e0-115">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4b8e0-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="4b8e0-116">TABLE_CAT</span></span>|<span data-ttu-id="4b8e0-117">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-117">String</span></span>|
|<span data-ttu-id="4b8e0-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="4b8e0-118">TABLE_SCHEM</span></span>|<span data-ttu-id="4b8e0-119">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-119">String</span></span>|
|<span data-ttu-id="4b8e0-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-120">TABLE_NAME</span></span>|<span data-ttu-id="4b8e0-121">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-121">String</span></span>|
|<span data-ttu-id="4b8e0-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-122">TABLE_TYPE</span></span>|<span data-ttu-id="4b8e0-123">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-123">String</span></span>|
|<span data-ttu-id="4b8e0-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-124">REMARKS</span></span>|<span data-ttu-id="4b8e0-125">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-125">String</span></span>|

### <a name="indexes"></a><span data-ttu-id="4b8e0-126">索引</span><span class="sxs-lookup"><span data-stu-id="4b8e0-126">Indexes</span></span>

|<span data-ttu-id="4b8e0-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4b8e0-127">ColumnName</span></span>|<span data-ttu-id="4b8e0-128">DataType</span><span class="sxs-lookup"><span data-stu-id="4b8e0-128">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4b8e0-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="4b8e0-129">TABLE_CAT</span></span>|<span data-ttu-id="4b8e0-130">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-130">String</span></span>|
|<span data-ttu-id="4b8e0-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="4b8e0-131">TABLE_SCHEM</span></span>|<span data-ttu-id="4b8e0-132">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-132">String</span></span>|
|<span data-ttu-id="4b8e0-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-133">TABLE_NAME</span></span>|<span data-ttu-id="4b8e0-134">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-134">String</span></span>|
|<span data-ttu-id="4b8e0-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-135">NON_UNIQUE</span></span>|<span data-ttu-id="4b8e0-136">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-136">Int16</span></span>|
|<span data-ttu-id="4b8e0-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4b8e0-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="4b8e0-138">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-138">String</span></span>|
|<span data-ttu-id="4b8e0-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-139">INDEX_NAME</span></span>|<span data-ttu-id="4b8e0-140">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-140">String</span></span>|
|<span data-ttu-id="4b8e0-141">TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-141">TYPE</span></span>|<span data-ttu-id="4b8e0-142">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-142">Int16</span></span>|
|<span data-ttu-id="4b8e0-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4b8e0-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="4b8e0-144">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-144">Int16</span></span>|
|<span data-ttu-id="4b8e0-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-145">COLUMN_NAME</span></span>|<span data-ttu-id="4b8e0-146">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-146">String</span></span>|
|<span data-ttu-id="4b8e0-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="4b8e0-147">ASC_OR_DESC</span></span>|<span data-ttu-id="4b8e0-148">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-148">String</span></span>|
|<span data-ttu-id="4b8e0-149">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="4b8e0-149">CARDINALITY</span></span>|<span data-ttu-id="4b8e0-150">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-150">Int32</span></span>|
|<span data-ttu-id="4b8e0-151">PAGES</span><span class="sxs-lookup"><span data-stu-id="4b8e0-151">PAGES</span></span>|<span data-ttu-id="4b8e0-152">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-152">Int32</span></span>|
|<span data-ttu-id="4b8e0-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="4b8e0-153">FILTER_CONDITION</span></span>|<span data-ttu-id="4b8e0-154">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-154">String</span></span>|
|<span data-ttu-id="4b8e0-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4b8e0-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="4b8e0-156">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-156">String</span></span>|
|<span data-ttu-id="4b8e0-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="4b8e0-158">Byte</span><span class="sxs-lookup"><span data-stu-id="4b8e0-158">Byte</span></span>|

### <a name="columns"></a><span data-ttu-id="4b8e0-159">資料行</span><span class="sxs-lookup"><span data-stu-id="4b8e0-159">Columns</span></span>

|<span data-ttu-id="4b8e0-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4b8e0-160">ColumnName</span></span>|<span data-ttu-id="4b8e0-161">DataType</span><span class="sxs-lookup"><span data-stu-id="4b8e0-161">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4b8e0-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="4b8e0-162">TABLE_CAT</span></span>|<span data-ttu-id="4b8e0-163">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-163">String</span></span>|
|<span data-ttu-id="4b8e0-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="4b8e0-164">TABLE_SCHEM</span></span>|<span data-ttu-id="4b8e0-165">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-165">String</span></span>|
|<span data-ttu-id="4b8e0-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-166">TABLE_NAME</span></span>|<span data-ttu-id="4b8e0-167">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-167">String</span></span>|
|<span data-ttu-id="4b8e0-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-168">COLUMN_NAME</span></span>|<span data-ttu-id="4b8e0-169">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-169">String</span></span>|
|<span data-ttu-id="4b8e0-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-170">DATA_TYPE</span></span>|<span data-ttu-id="4b8e0-171">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-171">Int16</span></span>|
|<span data-ttu-id="4b8e0-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-172">TYPE_NAME</span></span>|<span data-ttu-id="4b8e0-173">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-173">String</span></span>|
|<span data-ttu-id="4b8e0-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-174">COLUMN_SIZE</span></span>|<span data-ttu-id="4b8e0-175">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-175">Int32</span></span>|
|<span data-ttu-id="4b8e0-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4b8e0-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="4b8e0-177">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-177">Int32</span></span>|
|<span data-ttu-id="4b8e0-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="4b8e0-179">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-179">Int16</span></span>|
|<span data-ttu-id="4b8e0-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="4b8e0-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="4b8e0-181">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-181">Int16</span></span>|
|<span data-ttu-id="4b8e0-182">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-182">NULLABLE</span></span>|<span data-ttu-id="4b8e0-183">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-183">Int16</span></span>|
|<span data-ttu-id="4b8e0-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-184">REMARKS</span></span>|<span data-ttu-id="4b8e0-185">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-185">String</span></span>|
|<span data-ttu-id="4b8e0-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="4b8e0-186">COLUMN_DEF</span></span>|<span data-ttu-id="4b8e0-187">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-187">String</span></span>|
|<span data-ttu-id="4b8e0-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="4b8e0-189">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-189">Int16</span></span>|
|<span data-ttu-id="4b8e0-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="4b8e0-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="4b8e0-191">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-191">Int16</span></span>|
|<span data-ttu-id="4b8e0-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4b8e0-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="4b8e0-193">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-193">Int32</span></span>|
|<span data-ttu-id="4b8e0-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4b8e0-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="4b8e0-195">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-195">Int32</span></span>|
|<span data-ttu-id="4b8e0-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-196">IS_NULLABLE</span></span>|<span data-ttu-id="4b8e0-197">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-197">String</span></span>|
|<span data-ttu-id="4b8e0-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4b8e0-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="4b8e0-199">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-199">String</span></span>|
|<span data-ttu-id="4b8e0-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4b8e0-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="4b8e0-201">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-201">String</span></span>|
|<span data-ttu-id="4b8e0-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="4b8e0-203">Byte</span><span class="sxs-lookup"><span data-stu-id="4b8e0-203">Byte</span></span>|

### <a name="procedures"></a><span data-ttu-id="4b8e0-204">程序</span><span class="sxs-lookup"><span data-stu-id="4b8e0-204">Procedures</span></span>

|<span data-ttu-id="4b8e0-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4b8e0-205">ColumnName</span></span>|<span data-ttu-id="4b8e0-206">DataType</span><span class="sxs-lookup"><span data-stu-id="4b8e0-206">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4b8e0-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="4b8e0-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="4b8e0-208">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-208">String</span></span>|
|<span data-ttu-id="4b8e0-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="4b8e0-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="4b8e0-210">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-210">String</span></span>|
|<span data-ttu-id="4b8e0-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="4b8e0-212">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-212">String</span></span>|
|<span data-ttu-id="4b8e0-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="4b8e0-214">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-214">Int32</span></span>|
|<span data-ttu-id="4b8e0-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="4b8e0-216">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-216">Int32</span></span>|
|<span data-ttu-id="4b8e0-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="4b8e0-218">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-218">Int32</span></span>|
|<span data-ttu-id="4b8e0-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-219">REMARKS</span></span>|<span data-ttu-id="4b8e0-220">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-220">String</span></span>|
|<span data-ttu-id="4b8e0-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="4b8e0-222">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-222">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="4b8e0-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="4b8e0-223">ProcedureColumns</span></span>

|<span data-ttu-id="4b8e0-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4b8e0-224">ColumnName</span></span>|<span data-ttu-id="4b8e0-225">DataType</span><span class="sxs-lookup"><span data-stu-id="4b8e0-225">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4b8e0-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="4b8e0-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="4b8e0-227">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-227">String</span></span>|
|<span data-ttu-id="4b8e0-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="4b8e0-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="4b8e0-229">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-229">String</span></span>|
|<span data-ttu-id="4b8e0-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="4b8e0-231">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-231">String</span></span>|
|<span data-ttu-id="4b8e0-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-232">COLUMN_NAME</span></span>|<span data-ttu-id="4b8e0-233">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-233">String</span></span>|
|<span data-ttu-id="4b8e0-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-234">COLUMN_TYPE</span></span>|<span data-ttu-id="4b8e0-235">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-235">Int16</span></span>|
|<span data-ttu-id="4b8e0-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-236">DATA_TYPE</span></span>|<span data-ttu-id="4b8e0-237">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-237">Int16</span></span>|
|<span data-ttu-id="4b8e0-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-238">TYPE_NAME</span></span>|<span data-ttu-id="4b8e0-239">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-239">String</span></span>|
|<span data-ttu-id="4b8e0-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-240">COLUMN_SIZE</span></span>|<span data-ttu-id="4b8e0-241">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-241">Int32</span></span>|
|<span data-ttu-id="4b8e0-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4b8e0-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="4b8e0-243">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-243">Int32</span></span>|
|<span data-ttu-id="4b8e0-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="4b8e0-245">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-245">Int16</span></span>|
|<span data-ttu-id="4b8e0-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="4b8e0-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="4b8e0-247">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-247">Int16</span></span>|
|<span data-ttu-id="4b8e0-248">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-248">NULLABLE</span></span>|<span data-ttu-id="4b8e0-249">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-249">Int16</span></span>|
|<span data-ttu-id="4b8e0-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-250">REMARKS</span></span>|<span data-ttu-id="4b8e0-251">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-251">String</span></span>|
|<span data-ttu-id="4b8e0-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="4b8e0-252">COLUMN_DEF</span></span>|<span data-ttu-id="4b8e0-253">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-253">String</span></span>|
|<span data-ttu-id="4b8e0-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="4b8e0-255">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-255">Int16</span></span>|
|<span data-ttu-id="4b8e0-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="4b8e0-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="4b8e0-257">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-257">Int16</span></span>|
|<span data-ttu-id="4b8e0-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4b8e0-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="4b8e0-259">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-259">Int32</span></span>|
|<span data-ttu-id="4b8e0-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4b8e0-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="4b8e0-261">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-261">Int32</span></span>|
|<span data-ttu-id="4b8e0-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-262">IS_NULLABLE</span></span>|<span data-ttu-id="4b8e0-263">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-263">String</span></span>|
|<span data-ttu-id="4b8e0-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4b8e0-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="4b8e0-265">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-265">String</span></span>|
|<span data-ttu-id="4b8e0-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4b8e0-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="4b8e0-267">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-267">String</span></span>|
|<span data-ttu-id="4b8e0-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="4b8e0-269">Byte</span><span class="sxs-lookup"><span data-stu-id="4b8e0-269">Byte</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="4b8e0-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="4b8e0-270">ProcedureParameters</span></span>

|<span data-ttu-id="4b8e0-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4b8e0-271">ColumnName</span></span>|<span data-ttu-id="4b8e0-272">DataType</span><span class="sxs-lookup"><span data-stu-id="4b8e0-272">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4b8e0-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="4b8e0-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="4b8e0-274">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-274">String</span></span>|
|<span data-ttu-id="4b8e0-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="4b8e0-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="4b8e0-276">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-276">String</span></span>|
|<span data-ttu-id="4b8e0-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="4b8e0-278">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-278">String</span></span>|
|<span data-ttu-id="4b8e0-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-279">COLUMN_NAME</span></span>|<span data-ttu-id="4b8e0-280">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-280">String</span></span>|
|<span data-ttu-id="4b8e0-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-281">COLUMN_TYPE</span></span>|<span data-ttu-id="4b8e0-282">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-282">Int16</span></span>|
|<span data-ttu-id="4b8e0-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-283">DATA_TYPE</span></span>|<span data-ttu-id="4b8e0-284">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-284">Int16</span></span>|
|<span data-ttu-id="4b8e0-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-285">TYPE_NAME</span></span>|<span data-ttu-id="4b8e0-286">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-286">String</span></span>|
|<span data-ttu-id="4b8e0-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-287">COLUMN_SIZE</span></span>|<span data-ttu-id="4b8e0-288">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-288">Int32</span></span>|
|<span data-ttu-id="4b8e0-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4b8e0-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="4b8e0-290">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-290">Int32</span></span>|
|<span data-ttu-id="4b8e0-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="4b8e0-292">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-292">Int16</span></span>|
|<span data-ttu-id="4b8e0-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="4b8e0-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="4b8e0-294">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-294">Int16</span></span>|
|<span data-ttu-id="4b8e0-295">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-295">NULLABLE</span></span>|<span data-ttu-id="4b8e0-296">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-296">Int16</span></span>|
|<span data-ttu-id="4b8e0-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-297">REMARKS</span></span>|<span data-ttu-id="4b8e0-298">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-298">String</span></span>|
|<span data-ttu-id="4b8e0-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="4b8e0-299">COLUMN_DEF</span></span>|<span data-ttu-id="4b8e0-300">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-300">String</span></span>|
|<span data-ttu-id="4b8e0-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="4b8e0-302">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-302">Int16</span></span>|
|<span data-ttu-id="4b8e0-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="4b8e0-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="4b8e0-304">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-304">Int16</span></span>|
|<span data-ttu-id="4b8e0-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4b8e0-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="4b8e0-306">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-306">Int32</span></span>|
|<span data-ttu-id="4b8e0-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4b8e0-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="4b8e0-308">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-308">Int32</span></span>|
|<span data-ttu-id="4b8e0-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-309">IS_NULLABLE</span></span>|<span data-ttu-id="4b8e0-310">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-310">String</span></span>|
|<span data-ttu-id="4b8e0-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4b8e0-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="4b8e0-312">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-312">String</span></span>|
|<span data-ttu-id="4b8e0-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4b8e0-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="4b8e0-314">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-314">String</span></span>|
|<span data-ttu-id="4b8e0-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="4b8e0-316">Byte</span><span class="sxs-lookup"><span data-stu-id="4b8e0-316">Byte</span></span>|

## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="4b8e0-317">Microsoft Oracle ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="4b8e0-317">Microsoft Oracle ODBC Driver</span></span>

<span data-ttu-id="4b8e0-318">Microsoft SQL Server Oracle ODBC 驅動程式支援下列特定結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="4b8e0-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="4b8e0-319">資料表</span><span class="sxs-lookup"><span data-stu-id="4b8e0-319">Tables</span></span>

- <span data-ttu-id="4b8e0-320">資料行</span><span class="sxs-lookup"><span data-stu-id="4b8e0-320">Columns</span></span>

- <span data-ttu-id="4b8e0-321">程序</span><span class="sxs-lookup"><span data-stu-id="4b8e0-321">Procedures</span></span>

- <span data-ttu-id="4b8e0-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="4b8e0-322">ProcedureColumns</span></span>

- <span data-ttu-id="4b8e0-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="4b8e0-323">ProcedureParameters</span></span>

- <span data-ttu-id="4b8e0-324">檢視</span><span class="sxs-lookup"><span data-stu-id="4b8e0-324">Views</span></span>

- <span data-ttu-id="4b8e0-325">索引</span><span class="sxs-lookup"><span data-stu-id="4b8e0-325">Indexes</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="4b8e0-326">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="4b8e0-326">Tables and Views</span></span>

|<span data-ttu-id="4b8e0-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4b8e0-327">ColumnName</span></span>|<span data-ttu-id="4b8e0-328">DataType</span><span class="sxs-lookup"><span data-stu-id="4b8e0-328">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4b8e0-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4b8e0-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="4b8e0-330">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-330">String</span></span>|
|<span data-ttu-id="4b8e0-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="4b8e0-331">TABLE_OWNER</span></span>|<span data-ttu-id="4b8e0-332">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-332">String</span></span>|
|<span data-ttu-id="4b8e0-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-333">TABLE_NAME</span></span>|<span data-ttu-id="4b8e0-334">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-334">String</span></span>|
|<span data-ttu-id="4b8e0-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-335">TABLE_TYPE</span></span>|<span data-ttu-id="4b8e0-336">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-336">String</span></span>|
|<span data-ttu-id="4b8e0-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-337">REMARKS</span></span>|<span data-ttu-id="4b8e0-338">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-338">String</span></span>|

### <a name="columns"></a><span data-ttu-id="4b8e0-339">資料行</span><span class="sxs-lookup"><span data-stu-id="4b8e0-339">Columns</span></span>

|<span data-ttu-id="4b8e0-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4b8e0-340">ColumnName</span></span>|<span data-ttu-id="4b8e0-341">DataType</span><span class="sxs-lookup"><span data-stu-id="4b8e0-341">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4b8e0-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4b8e0-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="4b8e0-343">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-343">String</span></span>|
|<span data-ttu-id="4b8e0-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="4b8e0-344">TABLE_OWNER</span></span>|<span data-ttu-id="4b8e0-345">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-345">String</span></span>|
|<span data-ttu-id="4b8e0-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-346">TABLE_NAME</span></span>|<span data-ttu-id="4b8e0-347">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-347">String</span></span>|
|<span data-ttu-id="4b8e0-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-348">COLUMN_NAME</span></span>|<span data-ttu-id="4b8e0-349">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-349">String</span></span>|
|<span data-ttu-id="4b8e0-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-350">DATA_TYPE</span></span>|<span data-ttu-id="4b8e0-351">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-351">Int16</span></span>|
|<span data-ttu-id="4b8e0-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-352">TYPE_NAME</span></span>|<span data-ttu-id="4b8e0-353">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-353">String</span></span>|
|<span data-ttu-id="4b8e0-354">PRECISION</span><span class="sxs-lookup"><span data-stu-id="4b8e0-354">PRECISION</span></span>|<span data-ttu-id="4b8e0-355">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-355">Int32</span></span>|
|<span data-ttu-id="4b8e0-356">LENGTH</span><span class="sxs-lookup"><span data-stu-id="4b8e0-356">LENGTH</span></span>|<span data-ttu-id="4b8e0-357">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-357">Int32</span></span>|
|<span data-ttu-id="4b8e0-358">SCALE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-358">SCALE</span></span>|<span data-ttu-id="4b8e0-359">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-359">Int16</span></span>|
|<span data-ttu-id="4b8e0-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="4b8e0-360">RADIX</span></span>|<span data-ttu-id="4b8e0-361">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-361">Int16</span></span>|
|<span data-ttu-id="4b8e0-362">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-362">NULLABLE</span></span>|<span data-ttu-id="4b8e0-363">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-363">Int16</span></span>|
|<span data-ttu-id="4b8e0-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-364">REMARKS</span></span>|<span data-ttu-id="4b8e0-365">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-365">String</span></span>|
|<span data-ttu-id="4b8e0-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4b8e0-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="4b8e0-367">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-367">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="4b8e0-368">程序</span><span class="sxs-lookup"><span data-stu-id="4b8e0-368">Procedures</span></span>

|<span data-ttu-id="4b8e0-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4b8e0-369">ColumnName</span></span>|<span data-ttu-id="4b8e0-370">DataType</span><span class="sxs-lookup"><span data-stu-id="4b8e0-370">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4b8e0-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4b8e0-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="4b8e0-372">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-372">String</span></span>|
|<span data-ttu-id="4b8e0-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="4b8e0-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="4b8e0-374">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-374">String</span></span>|
|<span data-ttu-id="4b8e0-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="4b8e0-376">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-376">String</span></span>|
|<span data-ttu-id="4b8e0-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="4b8e0-378">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-378">Int16</span></span>|
|<span data-ttu-id="4b8e0-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="4b8e0-380">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-380">Int16</span></span>|
|<span data-ttu-id="4b8e0-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="4b8e0-382">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-382">Int16</span></span>|
|<span data-ttu-id="4b8e0-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-383">REMARKS</span></span>|<span data-ttu-id="4b8e0-384">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-384">String</span></span>|
|<span data-ttu-id="4b8e0-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="4b8e0-386">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-386">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="4b8e0-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="4b8e0-387">ProcedureColumns</span></span>

|<span data-ttu-id="4b8e0-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4b8e0-388">ColumnName</span></span>|<span data-ttu-id="4b8e0-389">DataType</span><span class="sxs-lookup"><span data-stu-id="4b8e0-389">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4b8e0-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4b8e0-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="4b8e0-391">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-391">String</span></span>|
|<span data-ttu-id="4b8e0-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="4b8e0-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="4b8e0-393">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-393">String</span></span>|
|<span data-ttu-id="4b8e0-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="4b8e0-395">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-395">String</span></span>|
|<span data-ttu-id="4b8e0-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-396">COLUMN_NAME</span></span>|<span data-ttu-id="4b8e0-397">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-397">String</span></span>|
|<span data-ttu-id="4b8e0-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-398">COLUMN_TYPE</span></span>|<span data-ttu-id="4b8e0-399">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-399">Int16</span></span>|
|<span data-ttu-id="4b8e0-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-400">DATA_TYPE</span></span>|<span data-ttu-id="4b8e0-401">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-401">Int16</span></span>|
|<span data-ttu-id="4b8e0-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-402">TYPE_NAME</span></span>|<span data-ttu-id="4b8e0-403">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-403">String</span></span>|
|<span data-ttu-id="4b8e0-404">PRECISION</span><span class="sxs-lookup"><span data-stu-id="4b8e0-404">PRECISION</span></span>|<span data-ttu-id="4b8e0-405">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-405">Int32</span></span>|
|<span data-ttu-id="4b8e0-406">LENGTH</span><span class="sxs-lookup"><span data-stu-id="4b8e0-406">LENGTH</span></span>|<span data-ttu-id="4b8e0-407">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-407">Int32</span></span>|
|<span data-ttu-id="4b8e0-408">SCALE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-408">SCALE</span></span>|<span data-ttu-id="4b8e0-409">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-409">Int16</span></span>|
|<span data-ttu-id="4b8e0-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="4b8e0-410">RADIX</span></span>|<span data-ttu-id="4b8e0-411">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-411">Int16</span></span>|
|<span data-ttu-id="4b8e0-412">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-412">NULLABLE</span></span>|<span data-ttu-id="4b8e0-413">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-413">Int16</span></span>|
|<span data-ttu-id="4b8e0-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-414">REMARKS</span></span>|<span data-ttu-id="4b8e0-415">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-415">String</span></span>|
|<span data-ttu-id="4b8e0-416">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="4b8e0-416">OVERLOAD</span></span>|<span data-ttu-id="4b8e0-417">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-417">Int32</span></span>|
|<span data-ttu-id="4b8e0-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4b8e0-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="4b8e0-419">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-419">Int32</span></span>|

## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="4b8e0-420">Microsoft Jet ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="4b8e0-420">Microsoft Jet ODBC Driver</span></span>

<span data-ttu-id="4b8e0-421">除了通用結構描述集合之外，Microsoft Jet ODBC 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="4b8e0-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="4b8e0-422">資料表</span><span class="sxs-lookup"><span data-stu-id="4b8e0-422">Tables</span></span>

- <span data-ttu-id="4b8e0-423">索引</span><span class="sxs-lookup"><span data-stu-id="4b8e0-423">Indexes</span></span>

- <span data-ttu-id="4b8e0-424">資料行</span><span class="sxs-lookup"><span data-stu-id="4b8e0-424">Columns</span></span>

- <span data-ttu-id="4b8e0-425">程序</span><span class="sxs-lookup"><span data-stu-id="4b8e0-425">Procedures</span></span>

- <span data-ttu-id="4b8e0-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="4b8e0-426">ProcedureColumns</span></span>

- <span data-ttu-id="4b8e0-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="4b8e0-427">ProcedureParameters</span></span>

- <span data-ttu-id="4b8e0-428">檢視</span><span class="sxs-lookup"><span data-stu-id="4b8e0-428">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="4b8e0-429">Tables 與 Views</span><span class="sxs-lookup"><span data-stu-id="4b8e0-429">Tables and Views</span></span>

|<span data-ttu-id="4b8e0-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4b8e0-430">ColumnName</span></span>|<span data-ttu-id="4b8e0-431">DataType</span><span class="sxs-lookup"><span data-stu-id="4b8e0-431">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4b8e0-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4b8e0-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="4b8e0-433">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-433">String</span></span>|
|<span data-ttu-id="4b8e0-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="4b8e0-434">TABLE_OWNER</span></span>|<span data-ttu-id="4b8e0-435">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-435">String</span></span>|
|<span data-ttu-id="4b8e0-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-436">TABLE_NAME</span></span>|<span data-ttu-id="4b8e0-437">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-437">String</span></span>|
|<span data-ttu-id="4b8e0-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-438">TABLE_TYPE</span></span>|<span data-ttu-id="4b8e0-439">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-439">String</span></span>|
|<span data-ttu-id="4b8e0-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-440">REMARKS</span></span>|<span data-ttu-id="4b8e0-441">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-441">String</span></span>|

### <a name="columns"></a><span data-ttu-id="4b8e0-442">資料行</span><span class="sxs-lookup"><span data-stu-id="4b8e0-442">Columns</span></span>

|<span data-ttu-id="4b8e0-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4b8e0-443">ColumnName</span></span>|<span data-ttu-id="4b8e0-444">DataType</span><span class="sxs-lookup"><span data-stu-id="4b8e0-444">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4b8e0-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4b8e0-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="4b8e0-446">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-446">String</span></span>|
|<span data-ttu-id="4b8e0-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="4b8e0-447">TABLE_OWNER</span></span>|<span data-ttu-id="4b8e0-448">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-448">String</span></span>|
|<span data-ttu-id="4b8e0-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-449">TABLE_NAME</span></span>|<span data-ttu-id="4b8e0-450">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-450">String</span></span>|
|<span data-ttu-id="4b8e0-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-451">COLUMN_NAME</span></span>|<span data-ttu-id="4b8e0-452">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-452">String</span></span>|
|<span data-ttu-id="4b8e0-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-453">DATA_TYPE</span></span>|<span data-ttu-id="4b8e0-454">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-454">Int16</span></span>|
|<span data-ttu-id="4b8e0-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-455">TYPE_NAME</span></span>|<span data-ttu-id="4b8e0-456">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-456">String</span></span>|
|<span data-ttu-id="4b8e0-457">PRECISION</span><span class="sxs-lookup"><span data-stu-id="4b8e0-457">PRECISION</span></span>|<span data-ttu-id="4b8e0-458">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-458">Int32</span></span>|
|<span data-ttu-id="4b8e0-459">LENGTH</span><span class="sxs-lookup"><span data-stu-id="4b8e0-459">LENGTH</span></span>|<span data-ttu-id="4b8e0-460">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-460">Int32</span></span>|
|<span data-ttu-id="4b8e0-461">SCALE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-461">SCALE</span></span>|<span data-ttu-id="4b8e0-462">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-462">Int16</span></span>|
|<span data-ttu-id="4b8e0-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="4b8e0-463">RADIX</span></span>|<span data-ttu-id="4b8e0-464">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-464">Int16</span></span>|
|<span data-ttu-id="4b8e0-465">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-465">NULLABLE</span></span>|<span data-ttu-id="4b8e0-466">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-466">Int16</span></span>|
|<span data-ttu-id="4b8e0-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-467">REMARKS</span></span>|<span data-ttu-id="4b8e0-468">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-468">String</span></span>|
|<span data-ttu-id="4b8e0-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4b8e0-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="4b8e0-470">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-470">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="4b8e0-471">程序</span><span class="sxs-lookup"><span data-stu-id="4b8e0-471">Procedures</span></span>

|<span data-ttu-id="4b8e0-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4b8e0-472">ColumnName</span></span>|<span data-ttu-id="4b8e0-473">DataType</span><span class="sxs-lookup"><span data-stu-id="4b8e0-473">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4b8e0-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4b8e0-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="4b8e0-475">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-475">String</span></span>|
|<span data-ttu-id="4b8e0-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="4b8e0-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="4b8e0-477">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-477">String</span></span>|
|<span data-ttu-id="4b8e0-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="4b8e0-479">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-479">String</span></span>|
|<span data-ttu-id="4b8e0-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="4b8e0-481">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-481">Int16</span></span>|
|<span data-ttu-id="4b8e0-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="4b8e0-483">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-483">Int16</span></span>|
|<span data-ttu-id="4b8e0-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="4b8e0-485">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-485">Int16</span></span>|
|<span data-ttu-id="4b8e0-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-486">REMARKS</span></span>|<span data-ttu-id="4b8e0-487">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-487">String</span></span>|
|<span data-ttu-id="4b8e0-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="4b8e0-489">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-489">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="4b8e0-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="4b8e0-490">ProcedureColumns</span></span>

|<span data-ttu-id="4b8e0-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4b8e0-491">ColumnName</span></span>|<span data-ttu-id="4b8e0-492">DataType</span><span class="sxs-lookup"><span data-stu-id="4b8e0-492">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4b8e0-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4b8e0-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="4b8e0-494">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-494">String</span></span>|
|<span data-ttu-id="4b8e0-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="4b8e0-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="4b8e0-496">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-496">String</span></span>|
|<span data-ttu-id="4b8e0-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="4b8e0-498">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-498">String</span></span>|
|<span data-ttu-id="4b8e0-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-499">COLUMN_NAME</span></span>|<span data-ttu-id="4b8e0-500">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-500">String</span></span>|
|<span data-ttu-id="4b8e0-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-501">COLUMN_TYPE</span></span>|<span data-ttu-id="4b8e0-502">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-502">Int16</span></span>|
|<span data-ttu-id="4b8e0-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-503">DATA_TYPE</span></span>|<span data-ttu-id="4b8e0-504">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-504">Int16</span></span>|
|<span data-ttu-id="4b8e0-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-505">TYPE_NAME</span></span>|<span data-ttu-id="4b8e0-506">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-506">String</span></span>|
|<span data-ttu-id="4b8e0-507">PRECISION</span><span class="sxs-lookup"><span data-stu-id="4b8e0-507">PRECISION</span></span>|<span data-ttu-id="4b8e0-508">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-508">Int32</span></span>|
|<span data-ttu-id="4b8e0-509">LENGTH</span><span class="sxs-lookup"><span data-stu-id="4b8e0-509">LENGTH</span></span>|<span data-ttu-id="4b8e0-510">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-510">Int32</span></span>|
|<span data-ttu-id="4b8e0-511">SCALE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-511">SCALE</span></span>|<span data-ttu-id="4b8e0-512">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-512">Int16</span></span>|
|<span data-ttu-id="4b8e0-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="4b8e0-513">RADIX</span></span>|<span data-ttu-id="4b8e0-514">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-514">Int16</span></span>|
|<span data-ttu-id="4b8e0-515">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-515">NULLABLE</span></span>|<span data-ttu-id="4b8e0-516">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-516">Int16</span></span>|
|<span data-ttu-id="4b8e0-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-517">REMARKS</span></span>|<span data-ttu-id="4b8e0-518">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-518">String</span></span>|
|<span data-ttu-id="4b8e0-519">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="4b8e0-519">OVERLOAD</span></span>|<span data-ttu-id="4b8e0-520">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-520">Int32</span></span>|
|<span data-ttu-id="4b8e0-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4b8e0-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="4b8e0-522">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-522">Int32</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="4b8e0-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="4b8e0-523">ProcedureParameters</span></span>

|<span data-ttu-id="4b8e0-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="4b8e0-524">ColumnName</span></span>|<span data-ttu-id="4b8e0-525">DataType</span><span class="sxs-lookup"><span data-stu-id="4b8e0-525">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="4b8e0-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="4b8e0-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="4b8e0-527">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-527">String</span></span>|
|<span data-ttu-id="4b8e0-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="4b8e0-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="4b8e0-529">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-529">String</span></span>|
|<span data-ttu-id="4b8e0-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="4b8e0-531">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-531">String</span></span>|
|<span data-ttu-id="4b8e0-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-532">COLUMN_NAME</span></span>|<span data-ttu-id="4b8e0-533">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-533">String</span></span>|
|<span data-ttu-id="4b8e0-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-534">COLUMN_TYPE</span></span>|<span data-ttu-id="4b8e0-535">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-535">Int16</span></span>|
|<span data-ttu-id="4b8e0-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-536">DATA_TYPE</span></span>|<span data-ttu-id="4b8e0-537">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-537">Int16</span></span>|
|<span data-ttu-id="4b8e0-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4b8e0-538">TYPE_NAME</span></span>|<span data-ttu-id="4b8e0-539">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-539">String</span></span>|
|<span data-ttu-id="4b8e0-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-540">COLUMN_SIZE</span></span>|<span data-ttu-id="4b8e0-541">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-541">Int32</span></span>|
|<span data-ttu-id="4b8e0-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4b8e0-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="4b8e0-543">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-543">Int32</span></span>|
|<span data-ttu-id="4b8e0-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="4b8e0-545">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-545">Int16</span></span>|
|<span data-ttu-id="4b8e0-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="4b8e0-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="4b8e0-547">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-547">Int16</span></span>|
|<span data-ttu-id="4b8e0-548">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-548">NULLABLE</span></span>|<span data-ttu-id="4b8e0-549">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-549">Int16</span></span>|
|<span data-ttu-id="4b8e0-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="4b8e0-550">REMARKS</span></span>|<span data-ttu-id="4b8e0-551">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-551">String</span></span>|
|<span data-ttu-id="4b8e0-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="4b8e0-552">COLUMN_DEF</span></span>|<span data-ttu-id="4b8e0-553">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-553">String</span></span>|
|<span data-ttu-id="4b8e0-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="4b8e0-555">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-555">Int16</span></span>|
|<span data-ttu-id="4b8e0-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="4b8e0-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="4b8e0-557">Int16</span><span class="sxs-lookup"><span data-stu-id="4b8e0-557">Int16</span></span>|
|<span data-ttu-id="4b8e0-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4b8e0-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="4b8e0-559">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-559">Int32</span></span>|
|<span data-ttu-id="4b8e0-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4b8e0-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="4b8e0-561">Int32</span><span class="sxs-lookup"><span data-stu-id="4b8e0-561">Int32</span></span>|
|<span data-ttu-id="4b8e0-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="4b8e0-562">IS_NULLABLE</span></span>|<span data-ttu-id="4b8e0-563">String</span><span class="sxs-lookup"><span data-stu-id="4b8e0-563">String</span></span>|

## <a name="see-also"></a><span data-ttu-id="4b8e0-564">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b8e0-564">See also</span></span>

- [<span data-ttu-id="4b8e0-565">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="4b8e0-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
