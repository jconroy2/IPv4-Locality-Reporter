# IPv4-Locality-Reporter
This project processes IPv4 addresses to generate locality-based reports. It reads data from a file, validates IPs, categorizes devices by locality, and outputs a summary report of valid entries and an error report for invalid ones. Features include file handling, dynamic memory allocation, and structured data processing.

Most computers on	the	internet	have	a	32	bit Internet	Protocol	Version	4	
(IPv4) address. As	reading	these addresses	would	be	difficult	using	
binary	or	hexadecimal	notation, IPv4 addresses	are usually	represented	
in	dotted	decimal notation.
For	purposes	of	representation,	the 32 bits composing	the	address may	
be	divided	into	four	octets	(bytes)	written	in	decimal	numbers, each
ranging	from	0	to	255,	and	concatenated	as	a	character	string	with	a	full	
stop	 (ASCII	46)	between	each	number.

The	first	two	components	of	the	address	indicate	the	computer’s	locality
on	the	network.	In	the	above	example,	the	locality	is	specified	by	the	
numbers	172 and	16.
Locally,	computers	are	often known	by	an alias (nickname) as	
well.	 You will design	and	write a	program	to	process	a	list	of	Internet	
addresses from	file	“CS222_Inet.txt”.		Your	program	should	read	this list	
of	addresses	and	nicknames	until a	sentinel	address	of	all	zeros	and	the
sentinel	nickname,	“NONE” is	reached.

Your program	will	generate	a	report	listing all computers	from	the	same	
locality---that	is,	each	computer with	matching	values	in	the	first	two
components of	the	address.	In	the	list,	the	computers	should	be	
identified	by	their	alias. The	report	will	also	list	the	number	of	valid	
locality	pairs	as	well	as	the	total	number	of	addresses	(see	sample	
report	below). The	report	will	be	saved	to	file	“222_Locality_Report”.	
An	error	report	will	also	be	generated	(discussed	below).	As	with	HW4,	
222_Locality_report	will	contain	the	user’s	name	and	current	date,	
along	with	the	generated	report	listing.

Example:
Hal	Greenwald	Nov 7,	2021
CS222	Network	Locality	Report
Address	total:5
Localities:	3
111.22
PLATTE
GREEN
131.250
JET
BAKER
172.66
WABASH

Program	structure	and	design:
Create	a	structure	type	called:
struct address_t
with	components	for	the	four	integers	of	an	IPv4	address	along	with a	
fifth	component	in	which	to	store	an	associated	alias	of	up	to	10	
characters.
Read	the	file	CS222_Inet.txt in	order	to	count	the	number	of	records	in	
the	file.	Provide	error	checking	in	order	to	ensure	that	each	integer	
portion	of	the	IP	address	falls	within	the	range	[0..255].	If	a	record	
contains	an	illegal	IP	address,	that	record	is	written to	the	file	
222_Error_report and	excluded from	the	222_Locality_Report 												
(see	HW5-test_set	example).	Once	the	record	count	has	been	
established,	rewind() the	file.
Dynamically	allocate the	proper	amount	of	memory	(using	malloc())	
to	store	a dynamically	allocated array	of	address_t	structures	based	on	
the	record	count.	
Reread	the	file	and	store	the	data	within	the	dynamically	allocated	array	
of	address_t structures.	Once	the	array	of	structures	has	been	populated,
close	the	CS222_Inet.txt	file.		

For	this	exercise	you	may	have	a	maximum	of	2	global	variables.
Include	at	least the	following	UDFs (You	may	define	your	own	prototypes):
a)	readDataFile			(Note:	With	the	exception	of	numeric	range	checking,	you	may	
											assume	that	the	data	file	is	syntactically	correct.)
b)	generateLocalityRpt
c) getDateAndTime			
