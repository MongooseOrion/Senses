<!-- =====================================================================
* Copyright (c) 2023, MongooseOrion.
* All rights reserved.
*
* The following code snippet may contain portions that are derived from
* OPEN-SOURCE communities, and these portions will be licensed with: 
*
* <NULL>
*
* If there is no OPEN-SOURCE licenses are listed, it indicates none of
* content in this Code document is sourced from OPEN-SOURCE communities. 
*
* In this case, the document is protected by copyright, and any use of
* all or part of its content by individuals, organizations, or companies
* without authorization is prohibited, unless the project repository
* associated with this document has added relevant OPEN-SOURCE licenses
* by github.com/MongooseOrion. 
*
* Please make sure using the content of this document in accordance with 
* the respective OPEN-SOURCE licenses. 
* 
* THIS CODE IS PROVIDED BY https://github.com/MongooseOrion. 
* FILE ENCODER TYPE: GBK
* ========================================================================
-->
# �Ϲ� PDS ��� IP ��ע������

PDS ������ĵ�д�ò�����ϸ���ܶ๦�ܺ����Ը�����Ҫ�Լ���������ʹ���߼����������ߵ����źŲ���Ū������������ƪ�ĵ����� PDS ��ĳЩ IP ��ע���������˵����

## DRM based FIFO

| �ź����� | ˵�� |
| :---: | :--- |
| wr_en��rd_en | �����ߺ���һ��ʱ�����ڣ�д����ʱ���򣩲Ż�д�����ݻ��߶������� |
| almost_full��almost_empty | �ڵ������õ�ֵʱͬʱ���ߣ���������һ��ʱ������ |
| wr_full��rd_empty | ��д�����һ�����ݣ����߶������һ�����ݺ�����ߣ����������һ������ͬʱ���� |

## FFT IP

  1. ���ٸ���Ҷ�任��FFT��IP �����������Ϊ 32 λ�����и� 16 λΪ�鲿���� 16 λΪʵ�������������Ϊ 64 λ�����и� 32 λΪ�鲿���� 32 λΪʵ��������Ľ���ֱ�ֻ�� 25 λΪ��Ч����λ���� 7 λΪ����λ��
  2. ��ʹ�÷�����Ҷ�任���ܣ��������������� 256 ����Ҳ���� 8 λ���Բ�Ҫ��