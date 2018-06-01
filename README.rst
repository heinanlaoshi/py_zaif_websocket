.. -*- mode: rst -*-

py_zaif_websocket
==========

''py_zaif_websocket''　は、仮想通貨取引所 Zaif のストリームプロトコル(Websocket)を使用して情報を取得するライブラリです。

Install
-------
Using pip

.. code::

  $ pip install git+https://github.com/mottio-cancer/py_zaif_websocket.git


Usage
-----

.. code:: python

  import py_zaif_websocket
  api = py_zaif_websocket.ZaifWebsocket(symbol=PRODUCT_CODE)


Example
-------

Order Book Infomaition
~~~~~~~~~~

.. code:: python

  # 現在のオーダー情報のスナップショットを取得します
  snapshot = api.get_board_snapshot()

Ticker
~~~~~~

.. code:: python

  # 最新のTicker情報を取得します
  ticker = api.get_ticker()

Execution Order 
~~~~~~~~~~~~~~~~


.. code:: python

  # 直近最大1000件の約定情報を取得します
  executions = api.get_excution()

  # 指定した''order_id''に対応した約定情報が存在すれば、その配列を返します
  executions = api.get_execution(order_id=ORDER_ID)
  # ''order_id''に対応する約定が配信されていない場合は空の配列を返却するので、
  # 下記のように注文の約定を待つことに使用できます
  while not api.get_execution(order_id=ORDER_ID):
    time.sleep(0.1)
  

More detail
~~~~~~~~~~~

ZaifのStreaming APIの仕様について詳しく知りたければ、下記を参照してください。
: http://techbureau-api-document.readthedocs.io/ja/latest/public/3_streaming.html

Author
------

@mottio-cancer (<mottio.cancer@gmail.com>)
