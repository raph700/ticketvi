'use client'

import Link from 'next/link'
import { Button } from "@/components/ui/button"
import { Card, CardContent, CardDescription, CardFooter, CardHeader, CardTitle } from "@/components/ui/card"
import { Ticket, ShoppingBag, Car, MessageCircle, Newspaper, Wallet, BookOpen, Gamepad2, ArrowRight, Mail, Phone, MapPin, Bot, Hotel, Utensils, Plane } from 'lucide-react'
import { motion, useScroll, useTransform } from 'framer-motion'
import { useRef } from 'react'
import { Input } from "@/components/ui/input"
import { Textarea } from "@/components/ui/textarea"

const features = [
  { name: 'Tickets', icon: Ticket, href: '/tickets', description: 'Book event tickets easily' },
  { name: 'Store', icon: ShoppingBag, href: '/store', description: 'Shop for various products' },
  { name: 'Rides', icon: Car, href: '/rides', description: 'Book rides and transportation' },
  { name: 'Messages', icon: MessageCircle, href: '/messages', description: 'Connect with others' },
  { name: 'News', icon: Newspaper, href: '/news', description: 'Stay updated with latest news' },
  { name: 'Wallet', icon: Wallet, href: '/wallet', description: 'Manage your finances' },
  { name: 'Blog', icon: BookOpen, href: '/blog', description: 'Read and write articles' },
  { name: 'Gamify', icon: Gamepad2, href: '/gamify', description: 'Enjoy games and earn rewards' },
  { name: 'Chat with AI', icon: Bot, href: '/chat-ai', description: 'Get instant AI assistance' },
  { name: 'Book a Hotel', icon: Hotel, href: '/hotels', description: 'Find and book accommodations' },
  { name: 'Discover Restaurants', icon: Utensils, href: '/restaurants', description: 'Explore local cuisines' },
  { name: 'Travel Planner', icon: Plane, href: '/travel', description: 'Plan your next adventure' },
]

export default function Home() {
  const ref = useRef(null)
  const { scrollYProgress } = useScroll({
    target: ref,
    offset: ["start start", "end start"]
  })
  const y = useTransform(scrollYProgress, [0, 1], ["0%", "50%"])

  return (
    <div className="min-h-screen bg-gradient-to-b from-purple-50 to-indigo-100">
      <section ref={ref} className="relative h-screen flex items-center justify-center overflow-hidden bg-gradient-to-r from-purple-600 to-indigo-600">
        <motion.div
          className="absolute inset-0 z-0"
          style={{
            backgroundImage: "url('/placeholder.svg?height=1080&width=1920')",
            backgroundSize: 'cover',
            backgroundPosition: 'center',
          }}
          initial={{ scale: 1.2, opacity: 0 }}
          animate={{ scale: 1, opacity: 0.2 }}
          transition={{ duration: 1.5 }}
        />
        <motion.div 
          style={{ y }} 
          className="relative z-10 text-center text-white max-w-4xl mx-auto px-4"
        >
          <motion.h1 
            className="text-6xl md:text-8xl font-bold mb-6 bg-clip-text text-transparent bg-gradient-to-r from-purple-200 to-pink-200"
            initial={{ opacity: 0, y: 20 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ duration: 0.8 }}
          >
            Welcome to TicketVibe
          </motion.h1>
          <motion.p 
            className="text-xl md:text-3xl mb-8 text-purple-100"
            initial={{ opacity: 0, y: 20 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ duration: 0.8, delay: 0.2 }}
          >
            Your ultimate destination for unforgettable experiences
          </motion.p>
          <motion.div
            initial={{ opacity: 0, y: 20 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ duration: 0.8, delay: 0.4 }}
            className="space-x-4"
          >
            <Button size="lg" className="bg-white text-purple-600 hover:bg-purple-100 transition-colors duration-200">
              Explore Events
            </Button>
            <Button size="lg" className="bg-purple-500 text-white hover:bg-purple-600 transition-colors duration-200">
              Sign Up Now
            </Button>
          </motion.div>
        </motion.div>
        <motion.div
          className="absolute bottom-0 left-0 right-0 h-32 bg-gradient-to-t from-purple-900 to-transparent"
          initial={{ opacity: 0 }}
          animate={{ opacity: 1 }}
          transition={{ duration: 1, delay: 0.5 }}
        />
      </section>

      <section className="container mx-auto px-4 py-16">
        <h2 className="text-3xl font-bold mb-8 text-center text-purple-800">Quick Access</h2>
        <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
          {features.map((feature, index) => (
            <motion.div
              key={feature.name}
              whileHover={{ scale: 1.05, rotateY: 5 }}
              whileTap={{ scale: 0.95 }}
              initial={{ opacity: 0, y: 20 }}
              animate={{ opacity: 1, y: 0 }}
              transition={{ duration: 0.5, delay: index * 0.1 }}
            >
              <Card className="h-full bg-white hover:shadow-xl transition-all duration-300 overflow-hidden">
                <CardHeader className="bg-gradient-to-r from-purple-500 to-indigo-500 text-white">
                  <CardTitle className="flex items-center justify-center">
                    <feature.icon className="h-8 w-8 mr-2" />
                    {feature.name}
                  </CardTitle>
                </CardHeader>
                <CardContent className="p-4">
                  <CardDescription className="text-center mb-4">{feature.description}</CardDescription>
                  <Link href={feature.href}>
                    <Button className="w-full bg-purple-600 hover:bg-purple-700 text-white transition-colors duration-200">
                      Explore {feature.name}
                      <ArrowRight className="ml-2 h-4 w-4" />
                    </Button>
                  </Link>
                </CardContent>
              </Card>
            </motion.div>
          ))}
        </div>
      </section>

      <section className="container mx-auto px-4 py-16">
        <h2 className="text-3xl font-bold mb-8 text-center text-purple-800">Latest Updates</h2>
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          <motion.div
            whileHover={{ scale: 1.03 }}
            initial={{ opacity: 0, y: 20 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ duration: 0.5 }}
          >
            <Card className="h-full bg-white hover:shadow-xl transition-all duration-300">
              <CardHeader>
                <CardTitle className="text-purple-700">New Store Items</CardTitle>
                <CardDescription>Check out the latest products in our store</CardDescription>
              </CardHeader>
              <CardContent>
                <p className="text-gray-600">Discover amazing deals on electronics, fashion, and more!</p>
              </CardContent>
              <CardFooter>
                <Button variant="outline" className="w-full group hover:bg-purple-100 transition-colors duration-200">
                  Visit Store
                  <ArrowRight className="ml-2 h-4 w-4 transition-transform group-hover:translate-x-1" />
                </Button>
              </CardFooter>
            </Card>
          </motion.div>
          <motion.div
            whileHover={{ scale: 1.03 }}
            initial={{ opacity: 0, y: 20 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ duration: 0.5, delay: 0.2 }}
          >
            <Card className="h-full bg-white hover:shadow-xl transition-all duration-300">
              <CardHeader>
                <CardTitle className="text-purple-700">Upcoming Events</CardTitle>
                <CardDescription>Don't miss out on exciting events</CardDescription>
              </CardHeader>
              <CardContent>
                <p className="text-gray-600">From concerts to sports, find tickets for all your favorite events.</p>
              </CardContent>
              <CardFooter>
                <Button variant="outline" className="w-full group hover:bg-purple-100 transition-colors duration-200">
                  Browse Events
                  <ArrowRight className="ml-2 h-4 w-4 transition-transform group-hover:translate-x-1" />
                </Button>
              </CardFooter>
            </Card>
          </motion.div>
          <motion.div
            whileHover={{ scale: 1.03 }}
            initial={{ opacity: 0, y: 20 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ duration: 0.5, delay: 0.4 }}
          >
            <Card className="h-full bg-white hover:shadow-xl transition-all duration-300">
              <CardHeader>
                <CardTitle className="text-purple-700">Travel Deals</CardTitle>
                <CardDescription>Plan your next adventure</CardDescription>
              </CardHeader>
              <CardContent>
                <p className="text-gray-600">Exclusive discounts on flights, hotels, and vacation packages.</p>
              </CardContent>
              <CardFooter>
                <Button variant="outline" className="w-full group hover:bg-purple-100 transition-colors duration-200">
                  Explore Deals
                  <ArrowRight className="ml-2 h-4 w-4 transition-transform group-hover:translate-x-1" />
                </Button>
              </CardFooter>
            </Card>
          </motion.div>
          <motion.div
            whileHover={{ scale: 1.03 }}
            initial={{ opacity: 0, y: 20 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ duration: 0.5, delay: 0.6 }}
          >
            <Card className="h-full bg-white hover:shadow-xl transition-all duration-300">
              <CardHeader>
                <CardTitle className="text-purple-700">AI Assistant Upgrade</CardTitle>
                <CardDescription>Enhanced AI capabilities for better assistance</CardDescription>
              </CardHeader>
              <CardContent>
                <p className="text-gray-600">Our AI assistant now supports voice commands and multi-language interactions.</p>
              </CardContent>
              <CardFooter>
                <Button variant="outline" className="w-full group hover:bg-purple-100 transition-colors duration-200">
                  Try AI Assistant
                  <ArrowRight className="ml-2 h-4 w-4 transition-transform group-hover:translate-x-1" />
                </Button>
              </CardFooter>
            </Card>
          </motion.div>
          <motion.div
            whileHover={{ scale: 1.03 }}
            initial={{ opacity: 0, y: 20 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ duration: 0.5, delay: 0.8 }}
          >
            <Card className="h-full bg-white hover:shadow-xl transition-all duration-300">
              <CardHeader>
                <CardTitle className="text-purple-700">New Restaurant Partners</CardTitle>
                <CardDescription>Expanded dining options for food lovers</CardDescription>
              </CardHeader>
              <CardContent>
                <p className="text-gray-600">We've partnered with top-rated restaurants to bring you more culinary experiences.</p>
              </CardContent>
              <CardFooter>
                <Button variant="outline" className="w-full group hover:bg-purple-100 transition-colors duration-200">
                  Discover Restaurants
                  <ArrowRight className="ml-2 h-4 w-4 transition-transform group-hover:translate-x-1" />
                </Button>
              </CardFooter>
            </Card>
          </motion.div>
          <motion.div
            whileHover={{ scale: 1.03 }}
            initial={{ opacity: 0, y: 20 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ duration: 0.5, delay: 1 }}
          >
            <Card className="h-full bg-white hover:shadow-xl transition-all duration-300">
              <CardHeader>
                <CardTitle className="text-purple-700">Wallet Integration</CardTitle>
                <CardDescription>Seamless payments across all services</CardDescription>
              </CardHeader>
              <CardContent>
                <p className="text-gray-600">Use your in-app wallet for quick and secure transactions on all our platforms.</p>
              </CardContent>
              <CardFooter>
                <Button variant="outline" className="w-full group hover:bg-purple-100 transition-colors duration-200">
                  Manage Wallet
                  <ArrowRight className="ml-2 h-4 w-4 transition-transform group-hover:translate-x-1" />
                </Button>
              </CardFooter>
            </Card>
          </motion.div>
        </div>
      </section>

      <section className="container mx-auto px-4 py-16 bg-white">
        <h2 className="text-3xl font-bold mb-8 text-center text-purple-800">About Us</h2>
        <div className="max-w-3xl mx-auto text-center">
          <p className="text-gray-600 mb-6">
            TicketVibe is your ultimate destination for unforgettable experiences. We strive to provide a seamless platform for discovering, booking, and enjoying events of all kinds.
          </p>
          <p className="text-gray-600 mb-6">
            Our mission is to connect people with their passions, from concerts and sports to cultural events and beyond. With TicketVibe, every ticket is a gateway to a memorable adventure.
          </p>
          <Button className="bg-purple-600 hover:bg-purple-700 text-white transition-colors duration-200">
            Learn More About Us
          </Button>
        </div>
      </section>

      <section className="container mx-auto px-4 py-16">
        <h2 className="text-3xl font-bold mb-8 text-center text-purple-800">Contact Us</h2>
        <div className="grid grid-cols-1 md:grid-cols-2 gap-8">
          <div>
            <h3 className="text-xl font-semibold mb-4 text-purple-700">Get in Touch</h3>
            <form className="space-y-4">
              <Input placeholder="Your Name" />
              <Input type="email" placeholder="Your Email" />
              <Textarea placeholder="Your Message" rows={4} />
              <Button className="bg-purple-600 hover:bg-purple-700 text-white transition-colors duration-200">
                Send Message
              </Button>
            </form>
          </div>
          <div>
            <h3 className="text-xl font-semibold mb-4 text-purple-700">Contact Information</h3>
            <div className="space-y-4">
              <div className="flex items-center">
                <Mail className="h-5 w-5 text-purple-600 mr-2" />
                <span className="text-gray-600">support@ticketvibe.com</span>
              </div>
              <div className="flex items-center">
                <Phone className="h-5 w-5 text-purple-600 mr-2" />
                <span className="text-gray-600">+1 (123) 456-7890</span>
              </div>
              <div className="flex items-center">
                <MapPin className="h-5 w-5 text-purple-600 mr-2" />
                <span className="text-gray-600">123 TicketVibe Avenue, Event City, 12345</span>
              </div>
            </div>
          </div>
        </div>
      </section>

      <footer className="bg-gradient-to-r from-purple-600 to-indigo-600 text-white py-12">
        <div className="container mx-auto px-4">
          <div className="grid grid-cols-1 md:grid-cols-4 gap-8">
            <div>
              <h3 className="text-lg font-semibold mb-4">About Us</h3>
              <p className="text-sm">TicketVibe is your gateway to unforgettable experiences and events.</p>
            </div>
            <div>
              <h3 className="text-lg font-semibold mb-4">Quick Links</h3>
              <ul className="space-y-2 text-sm">
                <li><Link href="/about" className="hover:text-purple-200 transition-colors duration-200">About</Link></li>
                <li><Link href="/contact" className="hover:text-purple-200 transition-colors duration-200">Contact</Link></li>
                <li><Link href="/privacy" className="hover:text-purple-200 transition-colors duration-200">Privacy Policy</Link></li>
                <li><Link href="/terms" className="hover:text-purple-200 transition-colors duration-200">Terms of Service</Link></li>
              </ul>
            </div>
            <div>
              <h3 className="text-lg font-semibold mb-4">Features</h3>
              <ul className="space-y-2 text-sm">
                <li><Link href="/tickets" className="hover:text-purple-200 transition-colors duration-200">Tickets</Link></li>
                <li><Link href="/events" className="hover:text-purple-200 transition-colors duration-200">Events</Link></li>
                <li><Link href="/venues" className="hover:text-purple-200 transition-colors duration-200">Venues</Link></li>
                <li><Link href="/artists" className="hover:text-purple-200 transition-colors duration-200">Artists</Link></li>
              </ul>
            </div>
            <div>
              <h3 className="text-lg font-semibold mb-4">Connect With Us</h3>
              <div className="flex space-x-4">
                <a href="#" className="hover:text-purple-200 transition-colors duration-200">
                  <svg className="w-6 h-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true"><path fillRule="evenodd" d="M22 12c0-5.523-4.477-10-10-10S2 6.477 2 12c0 4.991 3.657 9.128 8.438 9.878v-6.987h-2.54V12h2.54V9.797c0-2.506 1.492-3.89 3.777-3.89 1.094 0 2.238.195 2.238.195v2.46h-1.26c-1.243 0-1.63.771-1.63 1.562V12h2.773l-.443 2.89h-2.33v6.988C18.343 21.128 22 16.991 22 12z" clipRule="evenodd" /></svg>
                </a>
                <a href="#" className="hover:text-purple-200 transition-colors duration-200">
                  <svg className="w-6 h-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true"><path fillRule="evenodd" d="M12.315 2c2.43 0 2.784.013 3.808.06 1.064.049 1.791.218 2.427.465a4.902 4.902 0 011.772 1.153 4.902 4.902 0 011.153 1.772c.247.636.416 1.363.465 2.427.048 1.067.06 1.407.06 4.123v.08c0 2.643-.012 2.987-.06 4.043-.049 1.064-.218 1.791-.465 2.427a4.902 4.902 0 01-1.153 1.772 4.902 4.902 0 01-1.772 1.153c-.636.247-1.363.416-2.427.465-1.067.048-1.407.06-4.123.06h-.08c-2.643 0-2.987-.012-4.043-.06-1.064-.049-1.791-.218-2.427-.465a4.902 4.902 0 01-1.772-1.153 4.902 4.902 0 01-1.153-1.772c-.247-.636-.416-1.363-.465-2.427-.047-1.024-.06-1.379-.06-3.808v-.63c0-2.43.013-2.784.06-3.808.049-1.064.218-1.791.465-2.427a4.902 4.902 0 011.153-1.772A4.902 4.902 0 015.45 2.525c.636-.247 1.363-.416 2.427-.465C8.901 2.013 9.256 2 11.685 2h.63zm-.081 1.802h-.468c-2.456 0-2.784.011-3.807.058-.975.045-1.504.207-1.857.344-.467.182-.8.398-1.15.748-.35.35-.566.683-.748 1.15-.137.353-.3.882-.344 1.857-.047 1.023-.058 1.351-.058 3.807v.468c0 2.456.011 2.784.058 3.807.045.975.207 1.504.344 1.857.182.466.399.8.748 1.15.35.35.683.566 1.15.748.353.137.882.3 1.857.344 1.054.048 1.37.058 4.041.058h.08c2.597 0 2.917-.01 3.96-.058.976-.045 1.505-.207 1.858-.344.466-.182.8-.398 1.15-.748.35-.35.566-.683.748-1.15.137-.353.3-.882.344-1.857.048-1.055.058-1.37.058-4.041v-.08c0-2.597-.01-2.917-.058-3.96-.045-.976-.207-1.505-.344-1.858a3.097 3.097 0 00-.748-1.15 3.098 3.098 0 00-1.15-.748c-.353-.137-.882-.3-1.857-.344-1.023-.047-1.351-.058-3.807-.058zM12 6.865a5.135 5.135 0 110 10.27 5.135 5.135 0 010-10.27zm0 1.802a3.333 3.333 0 100 6.666 3.333 3.333 0 000-6.666zm5.338-3.205a1.2 1.2 0 110 2.4 1.2 1.2 0 010-2.4z" clipRule="evenodd" /></svg>
                </a>
                <a href="#" className="hover:text-purple-200 transition-colors duration-200">
                  <svg className="w-6 h-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true"><path d="M8.29 20.251c7.547 0 11.675-6.253 11.675-11.675 0-.178 0-.355-.012-.53A8.348 8.348 0 0022 5.92a8.19 8.19 0 01-2.357.646 4.118 4.118 0 001.804-2.27 8.224 8.224 0 01-2.605.996 4.107 4.107 0 00-6.993 3.743 11.65 11.65 0 01-8.457-4.287 4.106 4.106 0 001.27 5.477A4.072 4.072 0 012.8 9.713v.052a4.105 4.105 0 003.292 4.022 4.095 4.095 0 01-1.853.07 4.108 4.108 0 003.834 2.85A8.233 8.233 0 012 18.407a11.616 11.616 0 006.29 1.84" /></svg>
                </a>
              </div>
            </div>
          </div>
          <div className="mt-8 text-center text-sm">
            © {new Date().getFullYear()} TicketVibe. All rights reserved.
          </div>
        </div>
      </footer>
    </div>
  )
}
