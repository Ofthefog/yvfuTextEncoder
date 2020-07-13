# yvfuTextEncoder
The name comes from tumblr user yvfu, whose collaboration led to this idea. 

The purpose of this program is pass arbitrary files through a medium that normally only can send text, for example SMS or other chat programs. It is NOT ENCRYPTION. Encrypt your files using another method such as AES or RSA if you desire transfer security. This is also a very specific implementation - If you would like to have a general UNICODE conversion, take a look at https://github.com/qntm/base65536 . There is also one just for twitter here https://github.com/qntm/base2048 . What is left? Well, anything that uses a weridly constrictive set of acceptable charactors that aren't those.

The method is to create a hex dump of the file, compress it using a "keyfile" that represents the different possible values that can be sent ( unicode allows 143000, which means that FFFF can easily be converted to a single charactor ) over the chat program. The recipient will then use the same "keyfile" to decode the hex dump ( which is to say convert the base_(length of keyfile) into base_16 ), which can become the file on their end. It is assumed that the recipient will be able to possess this keyfile as it is simple text. This can be combined with file compression programs such as winrar or tar to further reduce transfer size, though this is only trading for later processing and possible data corruption.
