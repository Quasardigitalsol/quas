!DOCTYPE html>
<html lang="en">

<head>
    <meta http-equiv="content-type" content="text/html; charset=UTF-8">
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <meta name="description" content="">
    <meta name="keywords" content="">
    <link rel="icon" href="<?php echo SITE_URL ?>assets/images/favicon.png" sizes="32x32" type="image/png">
    <title>Masjid Anas Bin Malik</title>
    <?php include "header-files.php" ?>
</head>

<body>
    <main>
        <?php include "header.php" ?>
        <section>
            <div class="gap remove-bottom opc85">
                <div class="fixed-bg" style="background-image: url(<?php echo SITE_URL ?>assets/images/slide2-5.jpg);">
                </div>
                <div class="container">
                    <div class="page-title-wrap">
                        <h2 style="color:#fff;">Contact Us</h2>
                        <ul class="breadcrumbs">
                            <li><a href="index.php" title="" style="color:#fff;">Home</a></li>
                            <li style="color:#fff;">Contact Us</li>
                        </ul>
                    </div>
                </div>
            </div>
        </section>
        <section>
            <div class="gap">
                <div class="container">
                    <div class="sec-title text-center">
                        <div class="sec-title-inner">
                            <!-- <span>Get information</span> -->
                            <h3>Contact Information</h3>
                        </div>
                    </div>
                    <div class="contact-info-wrap text-center remove-ext3">
                        <div class="row">
                            <div class="col-md-4 col-sm-6 col-lg-4">
                                <div class="contact-info-box">
                                    <strong>Location</strong>
                                    <span>2904 Park Avenue East,
                                        Kansas City, MO 64109</span>
                                </div>
                            </div>
                            <div class="col-md-4 col-sm-6 col-lg-4">
                                <div class="contact-info-box">
                                    <strong>Contact Number</strong>
                                    <span>Telephone: 816 912 2041</span>
                                    <span>FAX: 816 912 2086</span>
                                </div>
                            </div>
                            <div class="col-md-4 col-sm-6 col-lg-4">
                                <div class="contact-info-box">
                                    <strong>Email</strong>
                                    <a href="mailto:info@masjidanasbinmalik.org"
                                        title="">info@masjidanasbinmalik.org</a>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        <section style="margin-bottom:50px">

            <div class="container">
                <div class="sec-title text-center">
                    <div class="sec-title-inner">
                        <!-- <span>Have Question</span> -->
                        <h3>Send Message</h3>
                    </div>
                </div>
                <div class="contact-form text-center"> 
                    <form name="frm_message" class="form-validate-jquery" id="frm_message" method="post"
                        novalidate="novalidate">
                        <div class="ajaxMsg"></div>
                        <div class="row mrg20">
                            <div class="col-md-6 col-sm-6 col-lg-6">
                                <input type="text" maxlength="25" name="name" id="name" lettersonly="true"
                                    class="form-control required" placeholder="Name">
                            </div>
                            <div class="col-md-6 col-sm-6 col-lg-6">
                                <input type="text" usphone="true" name="phone" id="phone" maxlength="10"
                                    class="form-control required" placeholder="Phone">
                            </div>
                            <div class="col-md-6 col-sm-6 col-lg-6">
                                <input type="email" maxlength="100" name="email" id="email"
                                    class="form-control required email" placeholder="Email">
                            </div>
                            <div class="col-md-6 col-sm-6 col-lg-6">
                                <input type="text" maxlength="50" name="subject" id="subject"
                                    class="form-control required subject" placeholder="Subject">
                            </div>
                            <div class="col-md-12 col-sm-12 col-lg-12">
                                <textarea name="message" id="message"
                                    class="form-control required message" placeholder="Message"></textarea>
                            </div>
                            <div class="col-md-12 col-sm-12 col-lg-12" style="margin-top:15px;">
                                <button class="thm-btn brd-rd40" type="submit">Submit</button>
                                <input type="hidden" name="action" value="message_form_submit">
                            </div>
                            <div class="col-md-12 col-sm-12 col-lg-12 ajaxMsgBot" style="margin-top:15px;">
                            </div>
                        </div>
                    </form>
                </div>
            </div>

        </section>
        <?php include "footer.php" ?>
    </main>
    <?php include "footer-files.php" ?>
</body>
<script>
$('#frm_message').submit(function(e) {
    e.preventDefault();
    if ($('#frm_message').valid()) {
        $('.ajaxMsgBot').html(
            '<h5>Processing...please wait</h5>'
            );
        var targetUrl = 'ajax/aj-message-form.php';
        var formDate = $(this).serialize();
        $.post(targetUrl, formDate, function(data, status) {
            if (status == 'success') {
                if (data.code == 1) {
                    $("#frm_message").trigger("reset");
                    $('.ajaxMsgBot').html('<h5>' + data.msg + '</h5>');
                }

                $('.ajaxMsgBot').html('<h5>' + data.msg + '</h5>');                
            } else {
                $('.ajaxMsgBot').html('Process faile. Please try later.');
            }
        }, 'json');
    }
});
</script>

</html>
