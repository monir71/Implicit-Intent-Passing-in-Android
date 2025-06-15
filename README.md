Simple but powerful:

        btnMsg = findViewById(R.id.btnMsg);
        btnEmail = findViewById(R.id.btnEmail);
        btnShare = findViewById(R.id.btnShare);
        btnDial = findViewById(R.id.btnDial);

        btnMsg.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Intent iMsg = new Intent();
                iMsg.setAction(Intent.ACTION_SENDTO);
                iMsg.setData(Uri.parse("smsto:"+Uri.encode("+8801710389323")));
                iMsg.putExtra("sms_body", "Please contact me as soon as possible!");
                startActivity(iMsg);
            }
        });

        btnEmail.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Intent iEmail = new Intent();
                iEmail.setAction(Intent.ACTION_SEND);
                iEmail.setType("message/rfc822");
                iEmail.putExtra(Intent.EXTRA_EMAIL, new String[] {"abc@gmail.com", "xyz@gmail.com"});
                iEmail.putExtra(Intent.EXTRA_SUBJECT, "Queries");
                iEmail.putExtra(Intent.EXTRA_TEXT, "Are you sure to proceed?");
                startActivity(Intent.createChooser(iEmail, "Send e-mail via"));
            }
        });

        btnShare.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Intent iShare = new Intent();
                iShare.setAction(Intent.ACTION_SEND);
                iShare.setType("text/plain");
                iShare.putExtra(Intent.EXTRA_TEXT, "Download this app, https://play.google.com/store/apps/details?id=com.adoriexpress");
                startActivity(Intent.createChooser(iShare, "Where to share..."));
            }
        });

        btnDial.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Intent iDial = new Intent();
                iDial.setAction(Intent.ACTION_DIAL);
                iDial.setData(Uri.parse("tel: +8801710389323"));
                startActivity(iDial);
            }
        });
