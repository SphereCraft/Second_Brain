23/10/2024 0638

Status #idea

Tags:

# EC2 Storage Options

Amazon Elastic Block Store (EBS) and Instance Store are the 2 main options.

Amazon EBS is like an external HDD that is connected to your PC. Its also a persistent storage, so even if your PC is switched off, it will stay active. Its good for documents, App data and photos, stuff you need to keep long term.

Instance Store, this is like the temporary storage in your PC (cache). It provides fast access to the data, but when the PC is off so is this storage. Its good for temporary files/data.
There are several types of EBS volume
	[[General purpose SSD (gp2)]]
	[[Provisioned IOPS SSD (io1)]]
	[[Throughput Optimised HDD (st1)]]
	[[Cold HDD]]
When selecting what EBS Volume type to use, consider these factors
	Performance requirements (iops and throughput)
	Durability Needs
	Budget constraints


# References
