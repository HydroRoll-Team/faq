CQ码
=====

.. attention::
    
    使用CQ码时请注意自己所用的设备类型，使用手表设备登录的话是无法发送和接收部分CQ码的。
    
    **所以以下内容均不针对手表端。**

CQ 码是一种特殊消息类型的文本格式，用于在QQ中发送各种各样的消息。这是它的基本语法::
        
    [CQ:类型, 参数=值, 参数=值]

或者::

    {
        "type": "类型",
        "data": {
            "参数": "值",
            "参数": "值"
        }
    }

----

at
---

::

    {
        "type": "at",
        "data": {
            "qq": "",
            "name": ""
        }
    }

.. tip::
    
    如果此人不在群内，可以使用name字段。
    
    .. code::
        
        [CQ:at,qq=123456,name=这人不在群里]
    
    显示: ``@这人不在群里``

:@用户: [CQ:at,qq=用户QQ]
:@全体成员: [CQ:at,qq=all]

----

表情
----

::

    {
        "type": "face",
        "data": {
            "id": ""
        }
    }


.. caution::
    
    黑色背景的为手机上可以显示，但电脑端会显示文字的表情，画X的为未知表情，应该是下架了。
    
    face不等于emoji，目前gocq框架不支持emoji。


:表情符号与id对应表如下: 

    ====================  ======================
    CQ 码列表 1            CQ 码列表 2  
    ====================  ======================
    |CQ_FACE_LIST_1|      |CQ_FACE_LIST_2| 
    ====================  ======================


.. |CQ_FACE_LIST_1| image:: https://files.hydroroll.team/files/image/face_id_list_1.jpg
    :alt: CQ 码列表 1
    :width: 50
.. |CQ_FACE_LIST_2| image:: https://files.hydroroll.team/files/image/face_id_list_2.jpg
    :alt: CQ 码列表 2
    :width: 50

----

图片
----

::

    {
        "type": "image",
        "data": {
            "file": ""
        }
    }

.. caution::

    图片最大不可超过30M，GIF动图超过300帧时无法发送。使用PNG格式发送图片不会被压缩。

发送时，``file`` 参数支持以下几种方案。

+ 绝对路径。
  例如 ``file:///C:\\Users\Alice\Pictures\1.png`` 。

+ 网络 `URL`。
  例如 ``https://www.baidu.com/img/PCtm_d9c8750bed0b3c7d089fa7d55720d6cf.png`` 。

+ `Base64` 编码。
  例如 ``base64://iVBORw0KGgoAAAANSUhEUgAAABQAAAAVCAIAAADJt1n/AAAAKElEQVQ4EWPk5+RmIBcwkasRpG9UM4mhNxpgowFGMARGEwnBIEJVAAAdBgBNAZf+QAAAAABJRU5ErkJggg==`` 。

:示例:

    ``[CQ:image,file=http://baidu.com/1.jpg,type=show,id=40004]``
