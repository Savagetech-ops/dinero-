import { useEffect, useState } from "react";
import { Button } from "@/components/ui/button";
import { motion } from "framer-motion";
import { FaRobot, FaTools } from "react-icons/fa";
import { SiWhatsapp } from "react-icons/si";

const services = [
  {
    title: "AI Solutions",
    description:
      "Custom AI systems, automation tools, and intelligent analytics to streamline your business.",
    image: "/ai-services.jpg",
    icon: <FaRobot className="text-green-600 w-8 h-8" />,
  },
  {
    title: "Tech Support",
    description:
      "Reliable and efficient tech support for software, hardware, networks, and more.",
    image: "/tech-support.jpg",
    icon: <FaTools className="text-blue-600 w-8 h-8" />,
  },
];

export default function Home() {
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    const timer = setTimeout(() => setLoading(false), 3000);
    return () => clearTimeout(timer);
  }, []);

  if (loading) {
    return (
      <div className="flex items-center justify-center h-screen bg-black text-white">
        <motion.h1
          initial={{ scale: 0 }}
          animate={{ scale: 1 }}
          transition={{ duration: 1 }}
          className="text-4xl font-bold"
        >
          DineroTech
        </motion.h1>
      </div>
    );
  }

  return (
    <div className="relative bg-gray-100 min-h-screen p-4">
      <div className="absolute inset-0 opacity-10 flex justify-center items-center pointer-events-none">
        <h1 className="text-6xl font-extrabold text-gray-300 transform -rotate-45">
          Certified by Savage Tech
        </h1>
      </div>

      <header className="text-center py-6 relative z-10">
        <h1 className="text-4xl font-bold text-gray-800">DineroTech</h1>
        <p className="text-gray-600 mt-2">
          Empowering Your Business with Smart AI Solutions and Reliable Tech Support
        </p>
        <p className="text-gray-500 text-sm mt-1">
          Contact us: <a href="mailto:dinerotools15@gmail.com" className="underline text-blue-600">dinerotools15@gmail.com</a>
        </p>
      </header>

      <section className="grid grid-cols-1 md:grid-cols-2 gap-6 max-w-5xl mx-auto relative z-10">
        {services.map((service, index) => (
          <motion.div
            key={index}
            whileHover={{ scale: 1.03 }}
            className="bg-white rounded-2xl shadow-md overflow-hidden"
          >
            <img src={service.image} alt={service.title} className="w-full h-48 object-cover" />
            <div className="p-4">
              <div className="flex items-center gap-2 mb-2">
                {service.icon}
                <h2 className="text-xl font-semibold text-gray-800">
                  {service.title}
                </h2>
              </div>
              <p className="text-gray-600 mb-4">{service.description}</p>
              <div className="space-y-2">
                <a
                  href="https://wa.me/2349021335159"
                  target="_blank"
                  rel="noopener noreferrer"
                >
                  <Button className="w-full gap-2 text-white bg-green-600 hover:bg-green-700">
                    <SiWhatsapp className="w-5 h-5" /> Chat on WhatsApp
                  </Button>
                </a>
                <a
                  href="https://wa.me/2349021335159"
                  target="_blank"
                  rel="noopener noreferrer"
                >
                  <Button className="w-full gap-2 text-white bg-blue-600 hover:bg-blue-700">
                    Make Payment
                  </Button>
                </a>
              </div>
            </div>
          </motion.div>
        ))}
      </section>

      <section className="mt-10 text-center relative z-10">
        <a
          href="https://wa.me/14697699166"
          target="_blank"
          rel="noopener noreferrer"
        >
          <Button className="gap-2 text-white bg-purple-600 hover:bg-purple-700">
            Chat with Admin
          </Button>
        </a>
      </section>

      <footer className="text-center text-gray-500 text-sm mt-10 relative z-10">
        &copy; {new Date().getFullYear()} DineroTech. All rights reserved.
      </footer>
    </div>
  );
}
