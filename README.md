package main

 

import (

    "log"

 

    "github.com/google/uuid"

    mail "github.com/xhit/go-simple-mail/v2"

)

 

var htmlBody = "<html><head><title>This is title</title></head><body><p>This is an email using Go</p><p><a href=https://google.com>please check google</a></body></html>"

 

func main() {

    server := mail.NewSMTPClient()

    server.Host = "smtp.taximail.com"

    server.Port = 587

    server.Username = "sm2317556"

    server.Password = "3c6i3uqY5vQQBdx"

    server.Encryption = mail.EncryptionTLS

 

    smtpClient, err := server.Connect()

    if err != nil {

        log.Fatal(err)

    }

 

    // Create email

    email := mail.NewMSG()

    email.SetFrom("From Me <vorrarit@gmail.com>")

    email.AddTo("vorrarit.l@kbtg.tech")

    messageId := uuid.NewString()

    email.SetSubject("{X-TM-Transc-Group|:|TEST TRANSACTIONAL::,X-TM-Ref-Msg-Id|:|" + messageId + "::,X-TM-Template|:|1755665276fa6cc539::,X-TM-From|:|taohooattack@gmail.com::,X-TM-From-Name|:|Taohoo Attack}")

 

    email.SetBody(mail.TextHTML, "{ \"CF_Subject\": \"Thank you for your order\", \"CF_Body\": \""+htmlBody+"\"}")

 

    raw := email.GetMessage()

    println(raw)

    err = email.Send(smtpClient)

    if err != nil {

        log.Fatal(err)

    }

}

 
# secret
https://viewer.diagrams.net/?tags=%7B%7D&highlight=0000ff&edit=_blank&layers=1&nav=1&title=demo.drawio#R7Vxbc9o4FP4t%2B8BM%2B2DG8g37kSRNu9t2N7Pt3p4ywhagxrYcWQTYX79Hlgy%2BAC0tCbC4kynW0f1cPo6OjunZ18niLcfZ9COLSNyzzGjRs296loUQMuFDUpaKEri%2BIkw4jXSjNeET%2FZdoou43mdGI5LWGgrFY0KxODFmaklDUaJhzNq83G7O4PmuGJ6RF%2BBTiuE39i0Ziqqi%2Ba67p7widTMuZkalrElw21oR8iiM2r5DsNz37mjMm1FOyuCaxZF7JF9XvdkvtamGcpOJbOlw9Ui96fP8zXvyF3v3y64ff74Mbw9FrE8tywySC%2Fesi42LKJizF8Zs19YqzWRoROaoJpXWbD4xlQERA%2FEKEWGph4plgQJqKJNa1ak450dataFLOZjwkO9ZfqgTmEyJ2tLNXDAdNJSwhgi%2BhHycxFvSpvg6sVWayarfmKjxoxu7BZE%2BN%2B4TjWTlTv5j8sWcP4SFmoG9TlsMGhrYpFegWZ7SYc8gJjhN4zCfhfUSe4ClmE5puFNsHPALrq7Eax3SSwnMInCUcCE%2BECwrTDXVFQqNISZXk9F88KsaTcs0YTUXBCfeq594AZcxSUWoGKstKxshZiVVOQBa9DbapB19bRFXg27WzLTU9umH2kecN1FjfLEk93J3cXmUsx1VdNEwZqLTwcgw2HuegYk1dWC3r%2B9UDtdRjGArGWyIGAMnk4yyJVYO1NAvJ37GcCsqkVEdMCJZsELeQJlpVEDYTMU3J9Qo%2BzV2SbJnoVuEg26wxdAXo8zWKlk2mFQD1zO2i%2ByEj9M8c6X4UwTbrvevWxYSsBv8Vsupeh9f9oKX7loTGu98%2BfVbYOBVCftMP5cwAizMxNXCU0NQAMAR176cszTiL%2BoCPUF%2BgZS7bDq708wAGvWUZSWlklE6CdSvYAzk5ELWfBUT9r4GoO%2FD9OvjZB8HUwKuPGtgvhqheZ%2BwbBOKYdWNflV%2FI2EuVrVi7K61dum6W%2BUVQ6aBz%2BN6CFYUhyfPPykrB45dM07pyDIOtGGjdgA9urUp1t5qr2XdsGzVclcN4QEHQGPbFzNWyj2GuZEHF37J73zRtXf6nKPt%2BoMs3Cz1%2BUVhWCneEU9i31K6Ky3TCxo8GDYfMa8j3mY3fbtn%2BEL7MgTLMspb468KdT6kgnzJccG3OcbYJd3%2FIW7Wdr3urK9foRdxVt8UucO9FggEOvRgmvxrBAcGbiGL%2FipJnsrbCRu9xxnSD9dO3dSlYbuSK59IPyzjZNhJOpEDSUZ59XzlW49yqxdQX2CC%2FIziSJje8aC6c9VaN%2FfYKB1OBwd3%2FvISz7znve18Rm8lMRjkxl8eVMeOJEWGBN%2Bp9Yx5zM%2Bl8WbenyiwMTh5nJBcGIOw573tPlRnIP47TiCV%2F%2FPHzjTz5ysNvB5TnudU9tf4Gi8sCyMvZamHYE5ISXsjYjORHZ91XLFq%2BWn0zvu68wjPe6p5gF8YUTnb3l%2FX9fjlbjZP8Pl%2FmgiSdRZ%2FrVr%2FPonMSchlkPOON77dv6%2B1HKx3a2ZfFx9T7OPz17XC%2BsLzp%2B2n2%2BPZ9OrZaoTFBFrJfJf6VC84eyDWL5ZXwTcpSua8xjeMGqYyKx2QsR9gaE98UbqsH5A4RcWvcO5obrof9DQG31gXlwSJuCLV4%2FRJR6BTW%2Fne1oGLQA7csr2PQRakahFbha9%2F2euvwNeqbqAxvf3v4OsL5tNgG0oU7LKBW6oUPPPFXQj9IhFvnbJx21g6yWiFYW6XtiBlP21ZvXtCdMtpt3GbfMuu3SYe5o7LrSTrOS11QDVqa8J4sw5jhh6PfXDhBHUi9Y19coONc5pUwavY9165DaaCu83ZhqSw1IXENsAEK6gBr23sD7KHvB18APYuuQ87xstJAo8%2F2HINGQlF5s3a7rT3yd7WHB7WCw%2BaHOC2DdvpKGjkpkw7mtLiefJCHTBOn8v9sNoppeP9AJEdkEqZE0DGd9JegiJcB%2FFuUap1N5NiDukAPgvzIqo9qoAZ%2BPWMyURv9fycRzY8O%2Fc1La2eDD%2F3C2N9O58twns8Zj%2FSZqywdwVh%2ByBh2S8K1ZBKJg5Bte%2B7A9uu%2Bj4OCfhAECLm%2BjTzbcp%2BJ%2B1bbYf2O8EmoDo1SWnwyegW8gNWY5cdr5epKoDHGOKHxUjV9R%2BInIiVTqc8LJJK1CGWLaoWaVNakjCc4rtQ9YU4xfIJ8MfjZJP9KuxBn25rMtcrLSmkbRU1M5LmmiAPQdNLuyXg2xake0tKOPRy5DQq2nerRzHI7RY3g0EHGocvRUhVYkHZYvH9SGUoqf33y1Viw3tEDheHkmOpMb2hLrrUb4fBhUmCN0ZCV5bpKTNWH15WVRiRkHMsccUNMafiQklwvj6ZU0JIHzbYVee1sV1lOrd0YPGXRZA4gaBbjZdlcJqHDw080ycD9w%2BnmKA%2B43apDb3Al8wXXNyBboi1S8Tco%2BQjEAFpQWTDo0yvDqNI14zp7OHF7OKJm7x2E7JTpxJXpksH1T%2BU3DDtIvXQr6CC1U6YOUg8AqTJ1p0PTCzeAc0LTTu86vTuG3p1odkZnL529dPZyQHvpjODEjeCSvXX92pBMKy76LVb%2Fiv12fvxlm8Y5fT90ynTiynTJOHtQ76Zn2cF2h6SE9OKVqQaoLzpIv3Qr7CC9U6YO0g8B6TsyMfZ8gQUA3Qt9Mhr36m%2BxAD3CxB%2BHvRN7lQU1Ul4da0Me3mBDHp7%2FbJlg7fxWr%2FrqQv3ntf5Pv6m1W1KWJ%2FP0TN90bROZvlPPKbUCWYsczxl4lmlbZfUe7yfUc1QP8ANa8jcNV78QrJqvf2fZfvMf
