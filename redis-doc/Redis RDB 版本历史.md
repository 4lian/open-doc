

**
���ߣ� coderbee (wen866595@163.com)   
ת����ע������
**



#  Redis RDB �汾��ʷ
����ĵ�������ת���ļ���ʽ�ڹ�ȥ�ĸı䡣

Redis ת���ļ���100%�����ݵġ��ɵ�ת���ļ����ǿ������°��Redis�﹤����


##  �汾6
����һ���汾��ziplistΪ����ʹ��һ���ɱ䳤�ȵı���ģʽ��
�����洢�� 16, 32, �� 64λ��������汾����ֿɱ䳤�ȱ���ϵͳ�ѱ���չ��

������������£�

1.  ����0 ��12����������[0-12]����������Ϊ��Ŀͷ����һ����
2.  ���� -128 �� 127����������[-128 - 127]�����洢��1���ֽ�
3.  ���� -2^32 �� 2^32 - 1����������[-2^32  -  2^32 - 1]�����洢��3���ֽ�

����ID�� <https://github.com/antirez/redis/issues/469>

ΪΪǨ�Ƶ��汾5��

1.  ��redis.conf������ `list-max-ziplist-entries`Ϊ0
2.  ����Redis������������`SAVE`����
3.  �༭dump.rdb�ļ�����ͷ����rdb�汾��Ϊ`REDIS0005`


##  �汾5
����汾���ļ�β������һ��8�ֽ�CRC-32У��ͣ����redis.conf�����У��ͣ����8�ֽ���0��

����ID�� <https://github.com/antirez/redis/issues/366>

ΪǨ�Ƶ��汾4��

1.  ɾ���ļ������8���ֽڣ����ֽ�`0xFF`��
2.  ��ͷ����rdb�汾��Ϊ`REDIS0004`


##  �汾4
����汾Ϊhashmap����һ���µı���--������ΪZiplist��Hashmap��������汾Ҳ������֮ǰ�汾ʹ�õ�Zipmap���롣

������ΪZiplist��Hashmap���ı�������=13��ֵ��ziplist����������list���ڽӵ���Ŀ����Ϊ��hashmap�ļ�ֵ�ԡ�

����ID��<https://github.com/antirez/redis/pull/285>

ΪǨ�Ƶ��汾3��

1.  ��redis.conf������`hash-max-ziplist-entries`Ϊ0��
2.  ����Redis������������`SAVE`����
3.  �༭dump.rdb�ļ�����ͷ����rdb�汾��Ϊ`REDIS0003`


##  �汾3
����汾���뾫ȷ������ļ���Ч���ޡ�

֮ǰ�汾�洢����Ч���޵ĸ�ʽΪ`0xFD <4�ֽ�ʱ���>`���ڰ汾3������Ч���޴洢Ϊ`0xFC <8�ֽ�ʱ���>`��
�����0xFD��0xFC�Ƿֱ�ָ������Ч����������ͺ���Ĳ����롣

����ID�� <https://github.com/antirez/redis/issues/169>

ΪǨ�Ƶ��汾2��

1.  ����㲻ʹ�ü���Ч���ޣ��򵥵ذ�ͷ���İ汾��Ϊ`REDIS0002`
2.  �����ʹ�ü���Ч���ޣ���Ȼ����Ǩ�ƣ����ǽ�������Ч���޾��ȵ���ʧ�����ң�Ǩ�ƽ��е㸴��
3.  ����ת���ļ����ÿ����ֵ���㽫��Ҫת��`0xFC <8�ֽ�ʱ���>` �� `0xFD <4�ֽ�ʱ���>`
4.  ת����ʱ����󣬰�ͷ����rdb�汾��Ϊ`REDIS0002`


##  �汾2
����汾ΪС��hashmap��list��set��������ı��롣

�ر��ǣ�����������ı������� -   
REDIS_RDB_TYPE_HASH_ZIPMAP = 9   
REDIS_RDB_TYPE_LIST_ZIPLIST = 10   
REDIS_RDB_TYPE_SET_INTSET = 11   
REDIS_RDB_TYPE_ZSET_ZIPLIST = 12   

�ύ�� <https://github.com/antirez/redis/commit/6b52ad87c05ca2162a2d21f1f5b5329bf52a7678>

ΪǨ�Ƶ��汾1��

1.  ��redis.conf����������`hash-max-zipmap-entries, list-max-ziplist-entries, set-max-intset-entries, zset-max-ziplist-entries` Ϊ0
2.  ����Redis������������`SAVE`����
3.  �༭dump.rdb�ļ�����ͷ����rdb�汾��Ϊ`REDIS0001`

