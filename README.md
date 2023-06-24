# I2C
In this Repository, we discuss how we have verified I2C protocol

Hi, there we gonna share views about what are the issues we got while verifying I2C protocol and discuss how we overcame those issues for multi-master and multi-slave.

Firstly I recommend you go through the specifications of the I2C protocol provided by NXP-semi conductors and I attached a document given by NXP semiconductors it may ask you to login so better google it.

https://www.scribd.com/document/655120660/I2C 

Here are some Keywords to start with.

    Keywords :  START
                STOP
                ACK
                NACK
                Data Validity
                Syncronization
                Arbitration
                7-bit slave
                10-bit slave
                Clock streching
                General Call Address

START: SCL is high while SDA is in a $fell state.

STOP: SCL is high and SDA is $rose.

ACK: ACK refers to the acceptance of value by the Transmitter or Receiver.

NACK: NACK refers to not accepting or rejecting the Master's Request.

Data Validity: Data should not change when SCL is high, it should only change when SCL is low. It says that you drive values at negedge and sample them                at posedge to check the data.
               
Synchronization: when multiple masters try to access or give the Start signal at the same instance then the clock should be synchronized so that only one                     master can perform. Both clocks of two masters will perform and operation then the resulting signal is equal to any one clock, the                         other clock is kept high so that and operation gives the same clock which is projected on SCL.

Arbitration: When Multiple masters Try to access, arbitration occurs between them and the win (It also does an AND operation same as clk                             synchronization).

7-bit slave: These are slave addresses which are 7-bit in size, so at max we can have 2**7 slaves.

10-bit slave: These are slave's address which are 10-bit in size, so at max we can have 2**10 slaves.

Clock stretching: To make things clear we are not going to do clock stretching, but if you are interested the clock is stretched by the slave by keeping                   the clock low in the meantime the slave performs other activities and serves interrupts.

General Call Address: In this, it gives software reset and updates some important hardware registers mostly it is updated by microcontroller.

In the following blogs we will discuss how we gonna code and discuss issues and then follow-up on them.
