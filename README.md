# csci4430-assignment-1--a-multi-client-file-transfer-application-solved
**TO GET THIS SOLUTION VISIT:** [CSCI4430  Assignment 1- A Multi-Client File Transfer Application Solved](https://www.ankitcodinghub.com/product/csci4430-assignment-1-a-multi-client-file-transfer-application-solved/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;92207&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;1&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (1 vote)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CSCI4430&nbsp; Assignment 1- A Multi-Client File Transfer Application Solved&nbsp;&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (1 vote)    </div>
    </div>
<div class="page" title="Page 1">
<div class="layoutArea">
<div class="column">
&nbsp;

1 Introduction

In this assignment, we will implement a multi-client file transfer application called MYFTP. MYFTP is a simplified version of the File Transfer Protocol (FTP). It includes the basic functionalities of FTP, such as file upload/download and file listing. It also enables multiple clients to simultaneously connect to the server at the same time. Our objective is to develop hands-on skills of socket programming and multi-threaded programming in C/C++.

2 Protocol Description 2.1 Overview

MYFTP is mainly composed of two entities: client and server. As their names suggest, the server hosts a file repository where the client can request to upload or download files.

MYFTP supports three main functions: (i) list the files that are stored on the server, (ii) upload files from the client to the server, or (iii) download files from the server to the client.

2.2 Protocol Messages

The client and the server will exchange protocol messages in order to perform the functions. All protocol messages are preceded with the protocol header shown below:

</div>
</div>
<div class="layoutArea">
<div class="column">
<pre>struct message_s {
    unsigned char protocol[5];
    unsigned char type;
    unsigned int length;
</pre>
<pre>} __attribute__ ((packed));
</pre>
</div>
<div class="column">
<pre>/* protocol string (5 bytes) *
/* type (1 byte) */
/* length (header + payload) (4 bytes) */
</pre>
</div>
</div>
<div class="layoutArea">
<div class="column">
The protocol field is always set to be the string that starts with the string “fubar”. The type field has different possible values as specified in Section 2.3. The length field is the length of the message (including the header and payload) to be sent over the network. The size of the payload is a variable depending on the message type. You can safely assume that the length is no larger than 232 − 1.

We add attribute ((packed)) to avoid data structure alignment and pack all variables together without any gap1. Defining a packed structure makes our life easier when we calculate the size of a message to be sent over the network.

2.3 Protocol Details

We now explain the functions that MYFTP supports. We also introduce the protocol messages that accompany each function, as well as the formats of the protocol messages. For now, let us assume that there is only one single client. Table 1 lists all protocol messages that are used.

1See http://en.wikipedia.org/wiki/Data_structure_alignment for details 1

</div>
</div>
</div>
<div class="page" title="Page 2">
<div class="layoutArea">
<div class="column">
LIST REQUEST

LIST REPLY

GET REQUEST

GET REPLY

PUT REQUEST

PUT REPLY

FILE DATA

</div>
<div class="column">
<pre>protocol
type
length
</pre>
<pre>protocol
type
length
payload
</pre>
<pre>protocol
type
length
payload
</pre>
<pre>protocol
type
length
</pre>
<pre>protocol
type
length
payload
</pre>
<pre>protocol
type
length
</pre>
<pre>protocol
type
length
payload
</pre>
</div>
<div class="column">
fubar

0xA1

header length

fubar

0xA2

header length + payload length

file names, in null-terminated string

fubar

0xB1

header length + payload length file name, in null-terminated string

fubar

0xB2 or 0xB3 header length

fubar

0xC1

header length + payload length file name, in null-terminated string

fubar

0xC2

header length

fubar

0xFF

header length + file size file payload

</div>
</div>
<div class="layoutArea">
<div class="column">
2.3.1 List Files

</div>
</div>
<div class="layoutArea">
<div class="column">
Table 1: Protocol messages

</div>
</div>
<div class="layoutArea">
<div class="column">
Suppose that the client wants to list all files that are stored in the server. The client will issue a command list. Then it will send a protocol message LIST REQUEST to the server. The server will reply a protocol message LIST REPLY, together with the list of available files.

All files are stored in a repository directory called data/, which is located under the working direc- tory of the server program. We assume that the directory has been created before the server starts. To list files in a directory, you may use the function readdir() (use man readdir to see its usage). All file names are delimited by the newline character ‘\n’.

2.3.2 File Download

Suppose that the client wants to download a file from the server. The client will issue a command get FILE, where FILE is the name of the file to be downloaded. It first sends a protocol message GET REQUEST to the server. The server will reply a protocol message GET REPLY with the type field set to 0xB2 if the file exists or 0xB3 otherwise. If the file exists, the server will send a FILE DATA message that contains the file content following the GET REPLY message.

Note that a file can be in either ASCII or binary mode. You should make sure that both ASCII and binary files are supported. Here, we assume that the file size is at most 1 GiB (which is equal to 230 bytes).

2.3.3 File Upload

Supposethattheclientwantstouploadafiletotheserver.Theclientwillissueacommandput FILE, where FILE is the name of the file to be uploaded. First, the client will check whether the file exists locally. If not, the client will display an error message saying the file doesn’t exist. If the file exists, then the client will send a protocol message PUT REQUEST to the server. The server will reply a protocol message PUT REPLY and awaits the file. Then the client will send a FILE DATA message

</div>
</div>
<div class="layoutArea">
<div class="column">
2

</div>
</div>
</div>
<div class="page" title="Page 3">
<div class="layoutArea">
<div class="column">
that contains the file content (we use the same FILE DATA message as in file download).

Here, we assume that the file to be uploaded resides in the same working directory as the client program. If the server has already stored the file before, the file will be overwritten. Note again that all

files are in ASCII or binary mode. We again assume that the file size is at most 1 GiB.

2.4 Interfaces

The server uses the following command-line interface:

<pre>sparc1&gt; ./myftpserver PORT_NUMBER
</pre>
You may fill in the port number as desired. The client uses the following command-line interface:

client&gt; ./myftpclient &lt;server ip addr&gt; &lt;server port&gt; &lt;list|get|put&gt; &lt;file&gt; Note that the file argument only exists for the get and put commands. You may define your own

output format for any error message.

2.5 Implementation Issues

The client and the server can reside in different machines with different operating systems (e.g., Linux vs. Unix), and all functions should remain correct. Make sure all byte ordering issues are properly addressed (see Tutorial notes).

The server may support multiple clients that may upload or download files simultaneously. We assume that no two clients will upload or download a file with the same file name simultaneously (to make your life easier), but it is possible that a client downloads a file that is previously uploaded by another client.

3 Milestones

Your implementation should have the following functions:

<ul>
<li>The client can list files in the repository directory of the server.</li>
<li>The client can download a file (either an ASCII or binary file) from the server. If the file doesn’t exist, the server replies with an error message.</li>
<li>The client can upload a file (either an ASCII or binary file) to the server. If the file doesn’t exist locally, the client displays an error message.</li>
<li>The client and the server can reside in different machines with different operating systems.</li>
<li>Now the server needs to support a general number N of active connections (assume that N ≤ 10). You will have to implement a multi-client version using multi-threading based on the pthread library.
Aside the above functions, you may make assumptions to address the features that are not mentioned in this specification.
</li>
</ul>
</div>
</div>
</div>
<div class="page" title="Page 4">
<div class="layoutArea">
<div class="column">
&nbsp;

</div>
</div>
</div>
